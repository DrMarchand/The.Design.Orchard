# Python Core Layout v0.1

Status: PROPOSED
Authority: © Design Orchard LLC

## Decision

All Python files that implement core system behavior must live beneath one governed Python-core root.

```text
core/
└── python/
    ├── atlas_schema/
    ├── activation/
    ├── evidence/
    ├── registry/
    ├── runtime/
    ├── security/
    ├── shared/
    └── tests/
```

The folder is the canonical home for reusable Python modules that belong to the system core.

## Responsibilities

```text
atlas_schema/
└── MariaDB inspection, schema normalization, node/edge generation, drift classification

activation/
└── approved activation handlers and command dispatch adapters

evidence/
└── evidence envelopes, hashes, receipts, and validation records

registry/
└── package, operation, version, Titan, and identity registry access

runtime/
└── runtime orchestration, job lifecycle, isolation adapters, and execution context

security/
└── authentication helpers, authorization checks, signature verification, and secret access interfaces

shared/
└── narrowly scoped utilities and common data models with no subsystem-specific authority

tests/
└── unit, integration, contract, and regression tests mirroring the core package structure
```

## Package law

Every Python subsystem must be an importable package.

```text
core/python/atlas_schema/
├── __init__.py
├── models.py
├── inspect_mariadb.py
├── normalize.py
├── diff.py
├── graph.py
├── receipts.py
└── tests/
```

Executable scripts must remain thin entry points. Business logic belongs in importable modules.

```text
commands/atlas_schema_inspect.py
        ↓ calls
core/python/atlas_schema/
```

## Prohibited structure

- unrelated `.py` files scattered at repository root;
- duplicate implementations of the same operation in multiple folders;
- executable scripts containing all core logic;
- secrets embedded in Python source;
- imports that bypass registered subsystem boundaries;
- generic `utils.py` files that accumulate unrelated behavior;
- tests stored separately from the code without a traceable package mapping.

## File registration

Each governed Python file must declare or be traceable to:

- subsystem;
- responsibility;
- owning package;
- callable entry points;
- mutation capability;
- dependencies;
- test coverage;
- version introduced;
- lifecycle state;
- evidence reference.

## Repository placement

The logical path is canonical even when repository layout requires a language source directory.

Preferred physical implementation:

```text
src/
└── drmarchand_core/
    ├── atlas_schema/
    ├── activation/
    ├── evidence/
    ├── registry/
    ├── runtime/
    ├── security/
    └── shared/

tests/
└── mirrors src/drmarchand_core/
```

The logical identity remains `core/python`. The `src/` layout is the recommended Python packaging implementation because it prevents accidental imports from the working directory.

## Validation

The layout is valid when:

- every core Python file maps to one registered subsystem;
- package imports work from an installed build, not only from the repository root;
- tests mirror the package structure;
- command entry points contain minimal orchestration code;
- no core Python implementation exists outside the governed root without an approved exception;
- ATLAS-SCHEMA Python modules live under the Atlas-schema package;
- package manifests and evidence records identify the exact source files used in each build.
