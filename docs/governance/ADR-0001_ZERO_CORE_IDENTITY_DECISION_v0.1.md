# ADR-0001 — Zero-Core Identity and Release-Family Decision v0.1

Status: PROPOSED
Authority: © Design Orchard LLC

## Core lineage

```text
DrMarchand’s ⚛️ OS™
└── holds DrMarchand’s 00 OS™ — FINITE core
    └── finite origin for DrMarchand’s ∞ OS™ ⚛︎ v0.0.0
```

DrMarchand’s ∞ OS™ ⚛︎ v0.0.0 is a versioned origin artifact derived from the FINITE core. It is not a separate OS identity.

## Release-family law

Each named family maps to one complete major-version range:

```yaml
product_identity: "DrMarchand’s ∞ OS™"
qualifier: "⚛︎"
release_families:
  - name: "Lionheart"
    major_generation: 1
    minimum: "v1.0.0"
    maximum: "v1.9.9"
  - name: "Phoenix"
    major_generation: 2
    minimum: "v2.0.0"
    maximum: "v2.9.9"
  - name: "Panther"
    major_generation: 3
    minimum: "v3.0.0"
    maximum: "v3.9.9"
  - name: "Timberwolf"
    major_generation: 4
    minimum: "v4.0.0"
    maximum: "v4.9.9"
  - name: "Sabertooth"
    major_generation: 5
    minimum: "v5.0.0"
    maximum: "v5.9.9"
```

## Canonical sequence

```text
DrMarchand’s ∞ OS™ ⚛︎ Lionheart   = v1.0.0 → v1.9.9
DrMarchand’s ∞ OS™ ⚛︎ Phoenix     = v2.0.0 → v2.9.9
DrMarchand’s ∞ OS™ ⚛︎ Panther     = v3.0.0 → v3.9.9
DrMarchand’s ∞ OS™ ⚛︎ Timberwolf  = v4.0.0 → v4.9.9
DrMarchand’s ∞ OS™ ⚛︎ Sabertooth  = v5.0.0 → v5.9.9
```

A family name identifies a major generation. A semantic version identifies one release within that family.

## Major-version boundaries

```text
Lionheart v1.9.9
        ↓
Phoenix v2.0.0
        ↓
Panther v3.0.0
        ↓
Timberwolf v4.0.0
        ↓
Sabertooth v5.0.0
```

Crossing a major-version boundary may change architecture, contracts, compatibility, migration requirements, or implementation strategy. It must preserve the evidence and identity history of the preceding family.

## Identity separation

The following fields must remain separate:

```yaml
identity: "DrMarchand’s ∞ OS™"
qualifier: "⚛︎"
release_family: "Panther"
version: "v3.0.0"
major_generation: 3
origin: "DrMarchand’s 00 OS™"
holding_layer: "DrMarchand’s ⚛️ OS™"
```

The family name must not be collapsed into its first release. For example, Panther is the entire `3.x` family, not only `v3.0.0`.

## Zero-name decision

- DrMarchand’s 00 OS™ remains the canonical FINITE core.
- DrMarchand’s 0 OS™ remains RESERVED and non-canonical.
- DrMarchand’s 000 OS™ remains RESERVED and non-canonical.

Neither reserved candidate may become canonical until implementation evidence proves a distinct responsibility, authority boundary, contract, lifecycle, and operational necessity.

## Validation

This decision is valid when:

- every `1.x` release resolves to Lionheart;
- every `2.x` release resolves to Phoenix;
- every `3.x` release resolves to Panther;
- every `4.x` release resolves to Timberwolf;
- every `5.x` release resolves to Sabertooth;
- `v2.9.9` resolves to Phoenix and `v3.0.0` resolves to Panther;
- `v3.9.9` resolves to Panther and `v4.0.0` resolves to Timberwolf;
- `v4.9.9` resolves to Timberwolf and `v5.0.0` resolves to Sabertooth;
- no release resolves to more than one family;
- Atlas stores product identity, qualifier, family, major generation, and exact version as separate fields;
- `0 OS` and `000 OS` remain RESERVED unless separately promoted.

## Current generation registry

| Major | Release family | Version range |
|---:|---|---|
| 1 | Lionheart | v1.0.0–v1.9.9 |
| 2 | Phoenix | v2.0.0–v2.9.9 |
| 3 | Panther | v3.0.0–v3.9.9 |
| 4 | Timberwolf | v4.0.0–v4.9.9 |
| 5 | Sabertooth | v5.0.0–v5.9.9 |
