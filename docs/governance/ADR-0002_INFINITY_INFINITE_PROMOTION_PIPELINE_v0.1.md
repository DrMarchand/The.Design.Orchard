# ADR-0002 — Infinity and Infinite Promotion Pipeline v0.1

Status: PROPOSED
Authority: © Design Orchard LLC

## Observed version roles

```text
DrMarchand’s ∞ OS™ ⚛︎ v0.0.1
DrMarchand’s ♾️ OS™ ⚛︎ v0.0.2
v0.0.3 — next sandbox candidate
```

The current lifecycle statement is:

> Once v0.0.3 is ready for sandbox, the validated work represented by v0.0.1 is promoted into the v0.0.2 working version.

## Decision

Promotion moves validated implementation, evidence, and approved changes forward. Promotion does not rename or overwrite an immutable version record.

```text
DrMarchand’s ∞ OS™ ⚛︎ v0.0.1
        │ validated changes promoted forward
        ▼
DrMarchand’s ♾️ OS™ ⚛︎ v0.0.2 — working version
        │ while the next independently identified candidate advances
        ▼
v0.0.3 — sandbox candidate
```

The source record `v0.0.1` remains preserved with its original identity, hashes, evidence, and rollback value.

The destination `v0.0.2` must be a separately built version artifact whose manifest explicitly records the promoted inputs from `v0.0.1`.

The `v0.0.3` candidate must also remain a separate artifact and must not become the sandbox build until its sandbox-readiness gate passes.

## Identity roles

The symbols remain semantically distinct:

- DrMarchand’s ∞ OS™ is INFINITE.
- DrMarchand’s ♾️ OS™ is INFINITY.

This ADR records the observed version assignments without claiming that INFINITE and INFINITY are merely lifecycle labels. Their broader architectural responsibilities remain separate and must be defined independently.

## Promotion gate

`v0.0.3` is ready for sandbox only when all required evidence exists:

- immutable source reference;
- build manifest;
- dependency lock state;
- configuration snapshot;
- successful required tests;
- security checks;
- artifact hashes;
- migration notes;
- rollback instructions;
- Atlas relationship record;
- Library custody receipt;
- explicit human approval where required.

Only after that gate passes may the coordinated promotion event occur.

## Coordinated promotion event

A promotion event must record:

```yaml
promotion_event:
  trigger: "v0.0.3 sandbox-ready"
  source_version: "DrMarchand’s ∞ OS™ ⚛︎ v0.0.1"
  destination_version: "DrMarchand’s ♾️ OS™ ⚛︎ v0.0.2"
  candidate_version: "v0.0.3"
  action: "promote validated changes forward"
  renames_source: false
  overwrites_source: false
  requires_new_build: true
  requires_new_evidence: true
```

## Prohibited behavior

- Renaming `v0.0.1` to `v0.0.2`.
- Reusing the same artifact hash under two version identities.
- Treating version promotion as proof that the destination build passed validation.
- Moving `v0.0.3` into sandbox without a recorded gate decision.
- Erasing the source version after promotion.
- Treating INFINITY and INFINITE as interchangeable because their versions participate in one promotion pipeline.

## Validation

The pipeline is valid when:

- all three version identities are separate records;
- `v0.0.1` remains retrievable after promotion;
- `v0.0.2` has a new build identity and manifest;
- the manifest identifies which changes came from `v0.0.1`;
- `v0.0.3` has an explicit sandbox-readiness decision;
- Atlas records PROMOTED_INTO, CANDIDATE_FOR, and SANDBOX_READY relationships separately;
- Library preserves each build and promotion receipt independently;
- rollback can restore the previous working state without reconstructing history.

## Unresolved point

The exact long-term division of responsibility between DrMarchand’s ∞ OS™ and DrMarchand’s ♾️ OS™ is not defined by this promotion rule alone. This ADR governs movement of versioned work, not the complete product architecture of either OS identity.
