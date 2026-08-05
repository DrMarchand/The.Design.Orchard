# ADR-0001 — Zero-Core Identity Decision v0.1

Status: PROPOSED
Authority: © Design Orchard LLC
Decision scope: DrMarchand’s 00 OS™, DrMarchand’s ⚛️ OS™, DrMarchand’s ∞ OS™ ⚛︎ v0.0.0, and the candidate identities DrMarchand’s 0 OS™ and DrMarchand’s 000 OS™.

## Context

DrMarchand’s 00 OS™ is the FINITE core.

The current proposed containment and derivation model is:

```text
DrMarchand’s ⚛️ OS™
└── holds DrMarchand’s 00 OS™ — FINITE core
    └── finite origin for DrMarchand’s ∞ OS™ ⚛︎ v0.0.0
```

DrMarchand’s ∞ OS™ ⚛︎ v0.0.0 is a versioned artifact or state derived from this finite foundation. The semantic version `v0.0.0` is not itself a separate OS identity.

## Decision

1. DrMarchand’s 00 OS™ remains the canonical FINITE core.
2. DrMarchand’s ⚛️ OS™ remains the proposed holding layer for that core.
3. DrMarchand’s ∞ OS™ ⚛︎ v0.0.0 is registered as originating from the FINITE core through the atomic holding layer.
4. DrMarchand’s 0 OS™ is RESERVED and not canonical.
5. DrMarchand’s 000 OS™ is RESERVED and not canonical.
6. Neither candidate may be implemented, named as a repository, or presented as an established component until a distinct responsibility is proven by implementation evidence.

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

## Identity and version law

```text
Identity: DrMarchand’s ∞ OS™
Qualifier: ⚛︎
Version: v0.0.0
Origin: DrMarchand’s 00 OS™ — FINITE core
Holding layer: DrMarchand’s ⚛️ OS™
```

Identity, qualifier, version, origin, and containment must be stored as separate fields. They must not be concatenated and treated as one uncontrolled name.

## Validation

This decision is valid when:

- Atlas records separate nodes for the holding layer, FINITE core, and versioned Infinite artifact;
- the derivation relationship is explicit;
- `0 OS` and `000 OS` are marked RESERVED rather than missing or established;
- repositories and filenames do not create those candidate identities prematurely;
- semantic version parsing does not infer component identity from zero counts.

## Consequence

The architecture remains minimal and extensible. Future implementation may promote one of the reserved candidates, but the burden of proof is on the new component rather than on preserving a speculative name.
