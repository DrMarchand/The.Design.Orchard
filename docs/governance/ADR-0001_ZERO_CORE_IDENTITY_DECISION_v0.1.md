# ADR-0001 — Zero-Core Identity Decision v0.1

Status: PROPOSED
Authority: © Design Orchard LLC
Decision scope: DrMarchand’s 00 OS™, DrMarchand’s ⚛️ OS™, DrMarchand’s ∞ OS™ ⚛︎ v0.0.0, DrMarchand’s ∞ OS™ ⚛︎ Lionheart, and the candidate identities DrMarchand’s 0 OS™ and DrMarchand’s 000 OS™.

## Context

DrMarchand’s 00 OS™ is the FINITE core.

The current proposed containment and derivation model is:

```text
DrMarchand’s ⚛️ OS™
└── holds DrMarchand’s 00 OS™ — FINITE core
    └── finite origin for DrMarchand’s ∞ OS™ ⚛︎ v0.0.0
        └── develops into DrMarchand’s ∞ OS™ ⚛︎ Lionheart
            └── release family v1.0.0 through v1.9.9
```

DrMarchand’s ∞ OS™ ⚛︎ v0.0.0 is a versioned artifact or state derived from this finite foundation. The semantic version `v0.0.0` is not itself a separate OS identity.

DrMarchand’s ∞ OS™ ⚛︎ Lionheart is the named release-family identity for the complete `1.x` generation. Lionheart begins at `v1.0.0` and remains the release-family name through `v1.9.9`.

## Decision

1. DrMarchand’s 00 OS™ remains the canonical FINITE core.
2. DrMarchand’s ⚛️ OS™ remains the proposed holding layer for that core.
3. DrMarchand’s ∞ OS™ ⚛︎ v0.0.0 is registered as originating from the FINITE core through the atomic holding layer.
4. DrMarchand’s ∞ OS™ ⚛︎ Lionheart is registered as the named release family for versions `v1.0.0` through `v1.9.9` inclusive.
5. Lionheart is not synonymous only with `v1.0.0`; each version in the `1.x` range is a member release of the Lionheart family.
6. `v2.0.0` is outside the Lionheart family unless a later explicit decision states otherwise.
7. DrMarchand’s 0 OS™ is RESERVED and not canonical.
8. DrMarchand’s 000 OS™ is RESERVED and not canonical.
9. Neither reserved candidate may be implemented, named as a repository, or presented as an established component until a distinct responsibility is proven by implementation evidence.

## Release-family law

```text
Product identity: DrMarchand’s ∞ OS™
Qualifier: ⚛︎
Release family: Lionheart
Version interval: >=1.0.0 and <=1.9.9
Major version: 1
```

The following forms are valid members of the same named generation:

```text
DrMarchand’s ∞ OS™ ⚛︎ Lionheart v1.0.0
DrMarchand’s ∞ OS™ ⚛︎ Lionheart v1.0.1
DrMarchand’s ∞ OS™ ⚛︎ Lionheart v1.5.0
DrMarchand’s ∞ OS™ ⚛︎ Lionheart v1.9.9
```

A version number identifies one release. Lionheart identifies the release family containing those releases.

The family name and version must therefore be stored separately:

```yaml
identity: "DrMarchand’s ∞ OS™"
qualifier: "⚛︎"
release_family: "Lionheart"
version: "v1.0.0"
major_generation: 1
family_range:
  minimum: "v1.0.0"
  maximum: "v1.9.9"
```

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

Separating Lionheart from individual versions prevents the opposite failure: treating a named generation as though it were only one build.

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
```

Identity, qualifier, family, version, origin, and containment must be stored as separate fields. They must not be concatenated and treated as one uncontrolled name.

## Validation

This decision is valid when:

- Atlas records separate nodes or typed records for the holding layer, FINITE core, Infinite product identity, Lionheart release family, and individual versioned releases;
- the derivation relationship is explicit;
- every `1.x` release resolves to Lionheart;
- no `0.x` or `2.x` release resolves to Lionheart without a separate approved exception;
- `0 OS` and `000 OS` are marked RESERVED rather than missing or established;
- repositories and filenames do not create those candidate identities prematurely;
- semantic version parsing does not infer component identity from zero counts;
- release-family parsing does not collapse Lionheart into `v1.0.0` alone.

## Consequence

The architecture remains minimal and extensible. Future implementation may promote one of the reserved candidates, but the burden of proof is on the new component rather than on preserving a speculative name.

Lionheart now has a precise technical meaning: the complete major-version-1 release family of DrMarchand’s ∞ OS™ ⚛︎.
