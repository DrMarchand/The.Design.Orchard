# ATLAS-SCHEMA Identity v0.1

Status: PROPOSED
Authority: © Design Orchard LLC

## Canonical identity

**ATLAS-SCHEMA** is the structural-observation and schema-lineage subsystem that translates relational database structure into DrMarchand’s ⚛︎ Atlas nodes and edges.

ATLAS-SCHEMA is not synonymous with:

- DrMarchand’s ⚛︎ Atlas;
- MariaDB;
- Python;
- the database being inspected;
- DrMarchand’s ⚙︎ Nɛuro-Forge Engine™.

## Core responsibility

```text
MariaDB metadata
        ↓ inspected by Python
ATLAS-SCHEMA structural manifest
        ↓ reconciled into
DrMarchand’s ⚛︎ Atlas
```

ATLAS-SCHEMA:

- reads approved MariaDB metadata;
- records database structure;
- turns columns into Atlas nodes;
- creates structural edges for containment, keys, indexes, constraints, and references;
- generates deterministic schema snapshots;
- detects and classifies schema drift;
- preserves rename, removal, supersession, and historical lineage;
- emits evidence for Library custody;
- emits observation events for Big Brother;
- does not independently authorize schema mutation.

## Canonical operation

```text
ATLAS_SCHEMA_INSPECT
```

Legacy or descriptive operation names such as `INSPECT_MARIADB_STRUCTURE` may remain as aliases during migration, but the canonical subsystem operation is `ATLAS_SCHEMA_INSPECT`.

## Canonical package fields

```yaml
package_id: "atlas-schema"
display_name: "ATLAS-SCHEMA"
classification: "STRUCTURAL_OBSERVER"
source_type: "RELATIONAL_SCHEMA"
initial_database_adapter: "MariaDB"
implementation_language: "Python"
output_target: "DrMarchand’s ⚛︎ Atlas"
default_mode: "READ_ONLY"
mutation_authority: false
```

## Structural graph law

```text
DATABASE CONTAINS TABLE
TABLE CONTAINS COLUMN
COLUMN REFERENCES COLUMN
COLUMN PARTICIPATES_IN CONSTRAINT
COLUMN PARTICIPATES_IN INDEX
COLUMN RENAMED_FROM COLUMN
COLUMN SUPERSEDES COLUMN
SCHEMA_SNAPSHOT OBSERVED COLUMN
```

Every column is represented as a distinct Atlas node with a stable identity that is not derived solely from the current column name.

## Authority boundaries

- MariaDB is the observed relational source.
- Python implements inspection, normalization, comparison, and evidence generation.
- ATLAS-SCHEMA owns the structural translation contract.
- Atlas owns graph representation and relationship resolution.
- The Engine governs approved migrations or mutations.
- Big Brother observes scans, drift, and reconciliation events.
- The Library preserves snapshots, diffs, manifests, and receipts.

## Validation

ATLAS-SCHEMA is valid when:

- the same database structure always produces the same normalized schema hash;
- each table and column has a deterministic structural record;
- every column resolves to an Atlas node;
- foreign-key and containment relationships resolve to Atlas edges;
- schema changes create append-only snapshots and classified differences;
- removed columns remain historically retrievable;
- row contents are excluded unless separately governed;
- the observer cannot mutate MariaDB in read-only mode;
- evidence and custody receipts are independently retrievable.
