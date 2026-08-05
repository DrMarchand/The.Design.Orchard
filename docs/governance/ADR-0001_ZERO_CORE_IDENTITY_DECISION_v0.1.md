# ADR-0001 — Shared Core, Titans, and Independent Version Lines v0.1

Status: PROPOSED
Authority: © Design Orchard LLC

## Decision summary

DrMarchand’s ∞ OS™ ⚛︎ v0.0.0 is the shared system core through which every Titan originates.

Each Titan has a distinct core version at the beginning of its major generation. From that core version, the Titan builds and holds its own independently governed version line.

```text
DrMarchand’s ⚛️ OS™
└── holds DrMarchand’s 00 OS™ — FINITE core
    └── produces DrMarchand’s ∞ OS™ ⚛︎ v0.0.0 — shared system core
        ├── Lionheart core v1.0.0
        │   └── builds and holds independent v1.x versions
        ├── Phoenix core v2.0.0
        │   └── builds and holds independent v2.x versions
        ├── Panther core v3.0.0
        │   └── builds and holds independent v3.x versions
        ├── Timberwolf core v4.0.0
        │   └── builds and holds independent v4.x versions
        └── Sabertooth core v5.0.0
            └── builds and holds independent v5.x versions
```

## Shared-core law

Every Titan must pass through and remain traceable to DrMarchand’s ∞ OS™ ⚛︎ v0.0.0.

The shared core provides the common origin, minimum system contract, identity continuity, and foundational compatibility surface.

A Titan may extend, replace, specialize, or deprecate capabilities above that shared core, but it must not rewrite or erase the shared-core lineage.

The required relationship is:

```text
DrMarchand’s ∞ OS™ ⚛︎ v0.0.0 IS_SHARED_CORE_FOR Titan
Titan DERIVES_FROM DrMarchand’s ∞ OS™ ⚛︎ v0.0.0
```

## Titan-core law

The first release of each major generation is that Titan’s core version:

| Titan | Titan core version | Independent version line |
|---|---:|---|
| Lionheart | v1.0.0 | v1.0.0–v1.9.9 |
| Phoenix | v2.0.0 | v2.0.0–v2.9.9 |
| Panther | v3.0.0 | v3.0.0–v3.9.9 |
| Timberwolf | v4.0.0 | v4.0.0–v4.9.9 |
| Sabertooth | v5.0.0 | v5.0.0–v5.9.9 |

The Titan core version is both:

- a separately built and evidenced semantic-version artifact; and
- the foundation for the remaining versions held by that Titan.

The Titan is not identical to its core version. The Titan holds the core version and all later versions in its major namespace.

```text
Titan HOLDS Titan Core Version
Titan HOLDS Subsequent Versions
Titan Core Version BUILDS_FOUNDATION_FOR Subsequent Versions
```

## Independent-line law

The Titans do not form a mandatory replacement chain in which each version must be built directly from the previous Titan’s final release.

All Titans share the `v0.0.0` system core. Each Titan then governs its own major-version lineage.

```text
Shared core v0.0.0
├── Lionheart lineage v1.x
├── Phoenix lineage v2.x
├── Panther lineage v3.x
├── Timberwolf lineage v4.x
└── Sabertooth lineage v5.x
```

A later Titan may intentionally inherit proven work from an earlier Titan, but cross-Titan inheritance must be declared as a dependency or migration relationship. It must not be assumed merely from major-version order.

## Version-build law

Every semantic version remains an independent governed build and must have its own:

- exact semantic version;
- Titan membership;
- shared-core reference;
- Titan-core reference;
- source commit or immutable source reference;
- build identifier and manifest;
- dependency lock state;
- configuration snapshot;
- migration contract;
- test and security evidence;
- artifact hashes;
- release notes;
- compatibility declaration;
- rollback or recovery instructions;
- Library custody receipt;
- lifecycle state.

A version may inherit code and architecture from its Titan core or another declared source, but it must produce independent evidence.

## Identity model

```yaml
product_identity: "DrMarchand’s ∞ OS™"
qualifier: "⚛︎"
shared_system_core: "v0.0.0"
titan: "Panther"
titan_major_generation: 3
titan_core_version: "v3.0.0"
version: "v3.2.4"
version_build_id: null
source_commit: null
artifact_hash: null
finite_origin: "DrMarchand’s 00 OS™"
holding_layer: "DrMarchand’s ⚛️ OS™"
```

Shared core, Titan, Titan core version, exact version, build identity, and finite origin must remain separate fields.

## Zero-name decision

- DrMarchand’s 00 OS™ remains the canonical FINITE core.
- DrMarchand’s 0 OS™ remains RESERVED and non-canonical.
- DrMarchand’s 000 OS™ remains RESERVED and non-canonical.

Neither reserved candidate may become canonical until implementation evidence proves a distinct responsibility, authority boundary, contract, lifecycle, and operational necessity.

## Validation

This decision is valid when:

- every Titan resolves to shared system core `v0.0.0`;
- each Titan has exactly one declared core version;
- Lionheart core resolves to `v1.0.0`;
- Phoenix core resolves to `v2.0.0`;
- Panther core resolves to `v3.0.0`;
- Timberwolf core resolves to `v4.0.0`;
- Sabertooth core resolves to `v5.0.0`;
- every semantic version exists as a separate build record;
- each version belongs to exactly one Titan;
- cross-Titan inheritance is explicit rather than inferred;
- Atlas stores shared-core, Titan, Titan-core, version, build, and derivation relationships separately;
- Library preserves evidence for every version independently while retaining shared-core and Titan lineage.
