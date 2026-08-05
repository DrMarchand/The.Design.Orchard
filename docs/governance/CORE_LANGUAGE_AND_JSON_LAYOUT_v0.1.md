# Core Language and JSON Layout v0.1

Status: PROPOSED
Authority: © Design Orchard LLC

## Decision

The system core is organized by runtime language and shared machine-readable contracts.

```text
core/
├── python/
├── node/
└── json/
```

Python and Node.js are neighboring execution lanes. JSON is a shared core contract and data-definition lane used by both.

## Canonical responsibilities

```text
core/python/
├── structural inspection
├── data processing
├── automation
├── evidence generation
├── database integration
└── Python-native runtime services

core/node/
├── API services
├── web and terminal activation adapters
├── event handling
├── package orchestration
├── interface integration
└── JavaScript/TypeScript runtime services

core/json/
├── manifests
├── JSON Schemas
├── registries
├── contracts
├── mappings
├── topology declarations
├── version records
├── Titan membership records
└── machine-readable configuration templates
```

JSON files do not execute themselves. They describe identity, structure, contracts, configuration, and permitted behavior consumed by governed runtimes.

## Recommended physical layout

```text
core/
├── python/
│   └── src/drmarchand_core/
│       ├── atlas_schema/
│       ├── activation/
│       ├── evidence/
│       ├── registry/
│       ├── runtime/
│       ├── security/
│       └── shared/
│
├── node/
│   ├── src/
│   │   ├── activation/
│   │   ├── api/
│   │   ├── evidence/
│   │   ├── registry/
│   │   ├── runtime/
│   │   ├── security/
│   │   └── shared/
│   ├── tests/
│   ├── package.json
│   └── tsconfig.json
│
└── json/
    ├── manifests/
    ├── schemas/
    ├── registries/
    ├── contracts/
    ├── mappings/
    ├── topology/
    ├── versions/
    └── examples/
```

## Node.js package law

Core Node.js behavior should be implemented in TypeScript unless a specific compatibility requirement justifies plain JavaScript.

Executable entry points must remain thin and call reusable modules.

```text
commands/activate-package.mjs
        ↓ calls
core/node/src/activation/
```

The Node.js lane must not duplicate Python behavior without a declared reason. Shared behavior should be defined by JSON contracts and implemented through language-specific adapters where necessary.

## JSON authority law

Each governed JSON file must have:

- a stable file identity;
- a declared schema;
- a schema version;
- an owning subsystem;
- a lifecycle state;
- validation rules;
- a canonical location;
- a change history;
- a source or evidence reference where applicable.

JSON content must be validated before use by Python, Node.js, a server, or a local terminal.

## Required JSON categories

```text
manifests/
└── package, build, activation, and evidence manifests

schemas/
└── JSON Schema definitions that validate core JSON documents

registries/
└── identities, operations, packages, Titans, versions, and adapters

contracts/
└── API, event, command, evidence, and migration contracts

mappings/
└── controlled translation maps between systems and identifiers

topology/
└── nodes, edges, containment, dependencies, and environment declarations

versions/
└── immutable version metadata and promotion lineage
```

## Cross-language contract

Python and Node.js must consume the same canonical JSON documents rather than maintaining separate uncontrolled copies.

```text
core/json/contracts/activation.contract.json
        ├── consumed by core/python/activation/
        └── consumed by core/node/src/activation/
```

A contract change is incomplete until:

- the JSON validates against its schema;
- Python contract tests pass;
- Node.js contract tests pass;
- compatibility impact is recorded;
- evidence is preserved.

## Prohibited structure

- JSON files scattered through unrelated folders without registration;
- configuration mixed with secrets;
- duplicate registries for Python and Node.js;
- executable logic encoded as arbitrary JSON strings;
- Node.js modules importing unvalidated JSON directly into privileged operations;
- JSON schemas that change without versioning;
- generated files silently overwriting canonical source files.

## Validation

The layout is valid when:

- all core Python code resolves under `core/python`;
- all core Node.js or TypeScript code resolves under `core/node`;
- all shared manifests, registries, schemas, and contracts resolve under `core/json`;
- Python and Node.js validate JSON through the same schemas;
- no secret is committed into the JSON core;
- executable entry points remain thin;
- duplicate language-specific contracts are rejected;
- each build identifies the exact Python, Node.js, and JSON inputs used.
