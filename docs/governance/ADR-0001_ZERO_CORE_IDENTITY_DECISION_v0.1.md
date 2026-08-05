# ADR-0001 — Zero-Core, Titan, and Version-Build Decision v0.1

Status: PROPOSED
Authority: © Design Orchard LLC

## Core lineage

```text
DrMarchand’s ⚛️ OS™
└── holds DrMarchand’s 00 OS™ — FINITE core
    └── finite origin for DrMarchand’s ∞ OS™ ⚛︎ v0.0.0
```

DrMarchand’s ∞ OS™ ⚛︎ v0.0.0 is a separately built origin artifact derived from the FINITE core. It is not a separate OS identity.

## Titan and version law

Lionheart, Phoenix, Panther, Timberwolf, and Sabertooth are Titans.

A Titan is the named container and lineage authority for one major-version family. A Titan is not itself a semantic-version build.

Each version must be designed, implemented, tested, packaged, released, verified, and preserved as its own artifact. The governing Titan holds the lineage, boundaries, shared identity, and version membership for those separately built releases.

```text
Titan
├── holds version vN.0.0
├── holds version vN.0.1
├── holds version vN.1.0
├── holds version ...
└── holds version vN.9.9
```

The required relationship is:

```text
Titan HOLDS Version
Version BELONGS_TO Titan
```

It is not:

```text
Titan IS Version
Version IS Titan
```

## Titan registry

```yaml
product_identity: "DrMarchand’s ∞ OS™"
qualifier: "⚛︎"
titans:
  - name: "Lionheart"
    major_generation: 1
    holds_versions:
      minimum: "v1.0.0"
      maximum: "v1.9.9"
  - name: "Phoenix"
    major_generation: 2
    holds_versions:
      minimum: "v2.0.0"
      maximum: "v2.9.9"
  - name: "Panther"
    major_generation: 3
    holds_versions:
      minimum: "v3.0.0"
      maximum: "v3.9.9"
  - name: "Timberwolf"
    major_generation: 4
    holds_versions:
      minimum: "v4.0.0"
      maximum: "v4.9.9"
  - name: "Sabertooth"
    major_generation: 5
    holds_versions:
      minimum: "v5.0.0"
      maximum: "v5.9.9"
```

## Canonical containment

```text
DrMarchand’s ∞ OS™ ⚛︎ Lionheart — Titan 1
├── DrMarchand’s ∞ OS™ ⚛︎ v1.0.0
├── DrMarchand’s ∞ OS™ ⚛︎ v1.0.1
├── DrMarchand’s ∞ OS™ ⚛︎ v1.1.0
└── ... through v1.9.9

DrMarchand’s ∞ OS™ ⚛︎ Phoenix — Titan 2
├── DrMarchand’s ∞ OS™ ⚛︎ v2.0.0
├── DrMarchand’s ∞ OS™ ⚛︎ v2.0.1
├── DrMarchand’s ∞ OS™ ⚛︎ v2.1.0
└── ... through v2.9.9

DrMarchand’s ∞ OS™ ⚛︎ Panther — Titan 3
└── separately built v3.x releases

DrMarchand’s ∞ OS™ ⚛︎ Timberwolf — Titan 4
└── separately built v4.x releases

DrMarchand’s ∞ OS™ ⚛︎ Sabertooth — Titan 5
└── separately built v5.x releases
```

## Version-build requirements

Every version is an independent governed build record and must have its own:

- exact semantic version;
- source commit or immutable source reference;
- build identifier;
- build manifest;
- dependency lock state;
- configuration snapshot;
- migration contract;
- test evidence;
- security evidence;
- artifact hashes;
- release notes;
- compatibility declaration;
- rollback or recovery instructions;
- custody receipt;
- Titan membership reference;
- lifecycle state.

A new version may inherit architecture, code, contracts, and assets from an earlier version, but inheritance does not make the builds identical. The new version must produce its own evidence.

## Titan responsibilities

A Titan holds:

- the major-generation identity;
- the permitted version namespace;
- shared architectural principles for that generation;
- compatibility and migration boundaries;
- the ordered lineage of its versions;
- generation-level documentation;
- generation-level acceptance requirements;
- the transition contract to the next Titan.

A Titan does not replace:

- source control history;
- individual version manifests;
- version-specific tests;
- version-specific evidence;
- version-specific release artifacts;
- version-specific rollback plans.

## Major-version transition law

```text
Lionheart
└── holds separately built v1.x releases
        ↓ transition contract
Phoenix
└── holds separately built v2.x releases
        ↓ transition contract
Panther
└── holds separately built v3.x releases
        ↓ transition contract
Timberwolf
└── holds separately built v4.x releases
        ↓ transition contract
Sabertooth
└── holds separately built v5.x releases
```

The next Titan begins with a new major-version build. The preceding Titan and all versions it holds remain preserved as historical lineage and evidence.

## Identity separation

The following fields must remain separate:

```yaml
product_identity: "DrMarchand’s ∞ OS™"
qualifier: "⚛︎"
titan: "Panther"
titan_major_generation: 3
version: "v3.2.4"
version_build_id: null
source_commit: null
artifact_hash: null
origin: "DrMarchand’s 00 OS™"
holding_layer: "DrMarchand’s ⚛️ OS™"
```

The Titan must not be collapsed into the version, and the version must not be collapsed into the Titan.

## Zero-name decision

- DrMarchand’s 00 OS™ remains the canonical FINITE core.
- DrMarchand’s 0 OS™ remains RESERVED and non-canonical.
- DrMarchand’s 000 OS™ remains RESERVED and non-canonical.

Neither reserved candidate may become canonical until implementation evidence proves a distinct responsibility, authority boundary, contract, lifecycle, and operational necessity.

## Validation

This decision is valid when:

- every `1.x` version belongs to Lionheart and exists as a separate build record;
- every `2.x` version belongs to Phoenix and exists as a separate build record;
- every `3.x` version belongs to Panther and exists as a separate build record;
- every `4.x` version belongs to Timberwolf and exists as a separate build record;
- every `5.x` version belongs to Sabertooth and exists as a separate build record;
- no version belongs to more than one Titan;
- no Titan is represented as one version artifact;
- each released version has its own source reference, manifest, evidence, hashes, custody receipt, and lifecycle state;
- Atlas stores Titan identity, major generation, exact version, build identity, and relationship as separate fields;
- Library preserves each version’s evidence independently while retaining Titan lineage;
- `0 OS` and `000 OS` remain RESERVED unless separately promoted.

## Current Titan registry

| Major | Titan | Held version namespace |
|---:|---|---|
| 1 | Lionheart | v1.0.0–v1.9.9 |
| 2 | Phoenix | v2.0.0–v2.9.9 |
| 3 | Panther | v3.0.0–v3.9.9 |
| 4 | Timberwolf | v4.0.0–v4.9.9 |
| 5 | Sabertooth | v5.0.0–v5.9.9 |
