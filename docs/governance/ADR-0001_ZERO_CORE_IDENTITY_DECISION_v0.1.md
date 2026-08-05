# ADR-0001 — Zero-Core Identity Decision v0.1

Status: PROPOSED
Authority: © Design Orchard LLC
Decision scope: DrMarchand’s 00 OS™, DrMarchand’s ⚛️ OS™, DrMarchand’s ∞ OS™ ⚛︎ v0.0.0, DrMarchand’s ∞ OS™ ⚛︎ Lionheart, DrMarchand’s ∞ OS™ ⚛︎ Phoenix, and the candidate identities DrMarchand’s 0 OS™ and DrMarchand’s 000 OS™.

## Context

DrMarchand’s 00 OS™ is the FINITE core.

The current containment and release-line model is:

```text
DrMarchand’s ⚛️ OS™
└── holds DrMarchand’s 00 OS™ — FINITE core
    └── finite origin for DrMarchand’s ∞ OS™ ⚛︎ v0.0.0
        ├── develops into DrMarchand’s ∞ OS™ ⚛︎ Lionheart
        │   └── release family v1.0.0 through v1.9.9
        └── advances into DrMarchand’s ∞ OS™ ⚛︎ Phoenix
            └── release family v2.0.0 through v2.9.9
```

DrMarchand’s ∞ OS™ ⚛︎ v0.0.0 is a versioned artifact or state derived from this finite foundation. The semantic version `v0.0.0` is not itself a separate OS identity.

DrMarchand’s ∞ OS™ ⚛︎ Lionheart is the named release-family identity for the complete `1.x` generation.

DrMarchand’s ∞ OS™ ⚛︎ Phoenix is the named release-family identity for the complete `2.x` generation. Phoenix begins at `v2.0.0` and remains the release-family name through `v2.9.9` unless a later explicit decision narrows or extends that range.

## Decision

1. DrMarchand’s 00 OS™ remains the canonical FINITE core.
2. DrMarchand’s ⚛️ OS™ remains the proposed holding layer for that core.
3. DrMarchand’s ∞ OS™ ⚛︎ v0.0.0 is registered as originating from the FINITE core through the atomic holding layer.
4. DrMarchand’s ∞ OS™ ⚛︎ Lionheart is the named release family for versions `v1.0.0` through `v1.9.9` inclusive.
5. DrMarchand’s ∞ OS™ ⚛︎ Phoenix is the named release family for versions `v2.0.0` through `v2.9.9` inclusive.
6. Lionheart is not synonymous only with `v1.0.0`; every version in the `1.x` range is a Lionheart member release.
7. Phoenix is not synonymous only with `v2.0.0`; every version in the `2.x` range is a Phoenix member release.
8. `v2.0.0` is the first Phoenix release and the boundary where the Lionheart family ends.
9. `v3.0.0` is outside Phoenix unless a later explicit decision states otherwise.
10. DrMarchand’s 0 OS™ is RESERVED and not canonical.
11. DrMarchand’s 000 OS™ is RESERVED and not canonical.
12. Neither reserved candidate may be implemented, named as a repository, or presented as an established component until a distinct responsibility is proven by implementation evidence.

## Release-family law

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
```

Valid forms include:

```text
DrMarchand’s ∞ OS™ ⚛︎ Lionheart v1.0.0
DrMarchand’s ∞ OS™ ⚛︎ Lionheart v1.9.9
DrMarchand’s ∞ OS™ ⚛︎ Phoenix v2.0.0
DrMarchand’s ∞ OS™ ⚛︎ Phoenix v2.9.9
```

A version number identifies one release. Lionheart and Phoenix identify release families containing multiple releases.

## Major-version transition law

The transition is explicit:

```text
Lionheart v1.9.9
        ↓ major-version boundary
Phoenix v2.0.0
```

A major-version boundary may change architecture, contracts, compatibility, migration requirements, or implementation strategy. It must not silently rewrite the identity or evidence history of the preceding family.

## Rationale

Creating DrMarchand’s 0 OS™ or DrMarchand’s 000 OS™ now would create ambiguity among:

- zero state;
- uninitialized state;
- bootstrap state;
- origin state;
- semantic version `v0.0.0`;
- the established FINITE identity `00`;
- release numbering and lifecycle numbering.

No distinct operational responsibility has yet been established for either candidate. Naming them now would create architecture without implementation need.

Separating release-family names from individual versions prevents Lionheart or Phoenix from being mistaken for only their first release.

## Reserved candidate tests

A candidate may become canonical only when all of the following are true:

- it has a responsibility not already owned by DrMarchand’s ⚛️ OS™, DrMarchand’s 00 OS™, or the version lifecycle;
- it has a defined authority boundary;
- it has an input and output contract;
- it has a lifecycle and failure state;
- it has implementation evidence;
- removing it would create a demonstrable architectural or operational gap;
- its symbol does not conflict with version notation or state notation;
- the human authority approves promotion from RESERVED to PROPOSED or ESTABLISHED.

## Candidate interpretations not adopted

Possible meanings remain unadopted:

- DrMarchand’s 0 OS™ as bootstrap or origin state;
- DrMarchand’s 000 OS™ as pre-origin, null, or uninitialized state.

These are semantic possibilities only. They are not current architecture.

## Identity, family, and version law

```text
Identity: DrMarchand’s ∞ OS™
Qualifier: ⚛︎
Origin version: v0.0.0
Origin: DrMarchand’s 00 OS™ — FINITE core
Holding layer: DrMarchand’s ⚛️ OS™
Named 1.x family: Lionheart
Lionheart range: v1.0.0 through v1.9.9
Named 2.x family: Phoenix
Phoenix range: v2.0.0 through v2.9.9
```

Identity, qualifier, family, version, origin, and containment must be stored as separate fields. They must not be concatenated and treated as one uncontrolled name.

## Validation

This decision is valid when:

- Atlas records separate nodes or typed records for the holding layer, FINITE core, Infinite product identity, Lionheart release family, Phoenix release family, and individual versioned releases;
- every `1.x` release resolves to Lionheart;
- every `2.x` release resolves to Phoenix;
- no `0.x`, `2.x`, or `3.x` release resolves to Lionheart without an approved exception;
- no `0.x`, `1.x`, or `3.x` release resolves to Phoenix without an approved exception;
- `v1.9.9` resolves to Lionheart and `v2.0.0` resolves to Phoenix;
- `0 OS` and `000 OS` remain RESERVED rather than missing or established;
- semantic-version parsing does not infer component identity from zero counts;
- release-family parsing does not collapse Lionheart into `v1.0.0` or Phoenix into `v2.0.0` alone.

## Consequence

Lionheart has a precise technical meaning: the complete major-version-1 release family of DrMarchand’s ∞ OS™ ⚛︎.

Phoenix has a precise technical meaning: the complete major-version-2 release family of DrMarchand’s ∞ OS™ ⚛︎.
