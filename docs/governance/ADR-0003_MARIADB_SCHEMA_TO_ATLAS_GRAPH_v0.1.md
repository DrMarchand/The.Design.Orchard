# ADR-0003 — MariaDB Schema Logging and Atlas Column-Node Graph v0.1

Status: PROPOSED
Authority: © Design Orchard LLC

## Decision summary

Python and MariaDB form the structural-observation layer for database topology.

MariaDB is the relational system being inspected. Python reads MariaDB metadata, detects structural changes, records schema history, and synchronizes the corresponding structure into DrMarchand’s ⚛︎ Atlas.

Columns are represented as Atlas nodes.

```text
MariaDB
└── database
    └── table
        └── column
            └── Atlas node
```

## Scope

The first governed scope is database structure, not ordinary row contents.

The structural model includes:

- database or catalog;
- schema where applicable;
- table;
- column;
- data type;
- nullability;
- default value;
- generated-column expression;
- primary key membership;
- foreign key membership;
- unique constraint membership;
- index membership;
- ordinal position;
- collation and character set;
- table engine;
- referenced table and column;
- creation, alteration, deprecation, and removal state.

Rows and business records do not automatically become Atlas nodes under this ADR.

## Authority separation

```text
MariaDB
└── source of observed relational structure

Python schema observer
├── reads metadata
├── normalizes structure
├── computes differences
├── emits evidence
└── requests Atlas reconciliation

DrMarchand’s ⚛︎ Atlas
├── holds structural nodes and edges
├── resolves current and historical relationships
└── does not execute database mutations

DrMarchand’s ⚙︎ Nɛuro-Forge Engine™
└── governs any approved mutation or migration execution

🪬 Big Brother
└── observes scans, drift, failures, and reconciliation events

📚 DrMarchand’s ⚛︎ Library™
└── preserves snapshots, diffs, manifests, and receipts
```

Python must not silently alter MariaDB structure merely because drift was detected.

## Node model

Every column becomes a distinct Atlas node with a stable identity independent of its display name.

```yaml
node_type: "database_column"
node_id: null
database: "example_db"
table: "users"
column: "email"
ordinal_position: 3
data_type: "varchar(255)"
nullable: false
default: null
primary_key: false
unique: true
lifecycle_state: "ACTIVE"
observed_at: null
source_fingerprint: null
```

A rename must not automatically create a new identity when evidence proves continuity. The observer should distinguish:

- rename;
- type change;
- constraint change;
- reorder;
- deletion;
- replacement by a different column.

When continuity cannot be proven, the old node should be retired and a new node proposed rather than silently merged.

## Edge model

Required structural edges include:

```text
DATABASE CONTAINS TABLE
TABLE CONTAINS COLUMN
COLUMN REFERENCES COLUMN
COLUMN PARTICIPATES_IN PRIMARY_KEY
COLUMN PARTICIPATES_IN FOREIGN_KEY
COLUMN PARTICIPATES_IN UNIQUE_CONSTRAINT
COLUMN PARTICIPATES_IN INDEX
COLUMN SUPERSEDES COLUMN
COLUMN RENAMED_FROM COLUMN
SCHEMA_SNAPSHOT OBSERVED COLUMN
```

Constraint and index objects may become nodes when they require their own lifecycle, evidence, or many-to-many relationships.

## Snapshot and history law

Each observation run must create an immutable schema snapshot record.

```yaml
schema_snapshot:
  snapshot_id: null
  source_system: "MariaDB"
  server_identity: null
  database_name: null
  observed_at: null
  observer_version: null
  schema_hash: null
  previous_snapshot_id: null
  change_count: 0
  evidence_receipt: null
```

The current state is resolved from snapshots and reconciliation records. History must not be overwritten.

The observer must classify changes such as:

- DATABASE_CREATED;
- DATABASE_REMOVED;
- TABLE_CREATED;
- TABLE_REMOVED;
- TABLE_RENAMED;
- COLUMN_CREATED;
- COLUMN_REMOVED;
- COLUMN_RENAMED;
- COLUMN_TYPE_CHANGED;
- COLUMN_NULLABILITY_CHANGED;
- COLUMN_DEFAULT_CHANGED;
- KEY_CHANGED;
- INDEX_CHANGED;
- FOREIGN_KEY_CHANGED;
- UNRESOLVED_DRIFT.

## Python observer flow

```text
1. Authenticate to MariaDB with read-only metadata privileges.
2. Read information_schema and approved system metadata.
3. Normalize identifiers and data types.
4. Build a deterministic structural manifest.
5. Hash the manifest.
6. Compare it with the previous accepted snapshot.
7. Classify differences.
8. Emit a schema-change evidence envelope.
9. Reconcile Atlas nodes and edges.
10. Preserve the snapshot, diff, and receipt in the Library.
11. Emit a Big Brother observation event.
```

## Activation model

The observer may be activated by:

- a local terminal command;
- an approved server endpoint;
- a scheduled job;
- a post-migration hook;
- a manual verification operation.

All activation paths must call the same registered operation and manifest.

```text
INSPECT_MARIADB_STRUCTURE
```

The operation is read-only by default.

## Minimum command contract

```text
dmos database inspect \
  --connection-id <registered-connection> \
  --database <database-name> \
  --emit-atlas-diff \
  --emit-library-receipt
```

Raw database passwords must not be accepted as command-line arguments or stored in GitHub.

## Risks

- Treating column names as stable IDs can corrupt lineage after renames.
- Mapping every row into Atlas would create uncontrolled graph growth and expose business data.
- Automatic schema mutation from the observer would collapse observation and execution authority.
- Reading only table names without constraints would produce an incomplete topology.
- Polling without deterministic hashes could generate false drift.
- Concurrent migrations could create inconsistent snapshots unless the observer records transaction and timing context.

## Validation

The first implementation is valid when:

- one MariaDB database can be inspected using read-only credentials;
- every table and column receives a deterministic structural record;
- every column is represented as an Atlas node;
- table-to-column containment edges are created;
- foreign-key column relationships are represented;
- two identical scans produce the same schema hash and no false changes;
- an added column produces one COLUMN_CREATED event;
- a removed column is preserved historically and marked inactive rather than erased;
- no row contents are copied into Atlas;
- no schema mutation can be executed by the observer;
- Library can retrieve the snapshot, diff, and receipt;
- Big Brother receives an observation event without command authority.
