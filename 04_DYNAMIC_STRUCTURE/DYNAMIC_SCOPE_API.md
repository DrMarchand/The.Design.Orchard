# ⚙︎ Dynamic Scope API Foundation

> **One parent. Multiple legitimate children. Shared inheritance. Distinct purpose. Explicit evidence. Controlled promotion.**

This page defines the first public, implementation-oriented contract for a reusable dynamic-scope API library inside the Design Orchard LLC repository.

The goal is not to publish every internal system detail. The goal is to expose a small, testable pattern that other software can implement safely:

```text
                 ⟦ PARENT SCOPE ⟧
                        │
                 shared properties
                        │
              ┌─────────┴─────────┐
              ▼                   ▼
         ⟦ CHILD α ⟧         ⟦ CHILD β ⟧
          + local Δ            + local Δ
              │                   │
              └─────────┬─────────┘
                        ▼
                 RESOLVED SCOPE
```

In compact form:

```text
resolved_child = inherited_parent + child_delta
```

The parent exists because the children share something real. The children remain separate because their differences still affect behavior.

---

## 1. Core rule

A dynamic-scope implementation MUST preserve both relationships at the same time:

```text
RELATED(child_a, child_b) = true
EQUAL(child_a, child_b)   = false
```

A child may inherit common identity context, provenance, authority context, defaults, or validation rules from a parent without becoming identical to its sibling.

The implementation MUST NOT flatten sibling scopes into one object merely because they share a parent.

---

## 2. Minimal object model

A portable scope object can begin with this shape:

```json
{
  "id": "scope.child.alpha",
  "parent_id": "scope.parent",
  "namespace": "example.alpha",
  "display_name": "Child Alpha",
  "purpose": "example-purpose",
  "delta": {
    "mode": "alpha"
  },
  "state": "DRAFT",
  "evidence": []
}
```

The parent can provide shared values:

```json
{
  "id": "scope.parent",
  "namespace": "example",
  "authority_context": "root-authority",
  "provenance": "source-object-001",
  "defaults": {
    "validation_required": true,
    "human_gate": true
  }
}
```

The library resolves, but does not erase, the child delta.

---

## 3. Reference resolution contract

```javascript
export function resolveScope(parent, child) {
  if (!parent || !child) throw new Error("parent and child are required");
  if (child.parent_id !== parent.id) throw new Error("parent relationship mismatch");

  return {
    ...parent,
    ...child,
    inherited: {
      authority_context: parent.authority_context,
      provenance: parent.provenance,
      defaults: parent.defaults ?? {}
    },
    delta: child.delta ?? {}
  };
}
```

The important behavior is not object spreading itself. The contract is:

```text
1. identify the parent
2. validate the parent-child edge
3. inherit only allowed fields
4. preserve the child's local delta
5. preserve the child's identity
6. return a resolved view
```

A production implementation SHOULD use explicit inheritance allowlists instead of blindly copying every parent field.

---

## 4. Selective inheritance

Recommended field classes:

```text
INHERITABLE
├── provenance
├── authority_context
├── default validation policy
├── common metadata
└── shared schema version

LOCAL
├── id
├── namespace
├── purpose
├── mode
├── workflow state
└── representation

NON-INHERITABLE BY DEFAULT
├── credentials
├── secrets
├── proof of health
├── verification state
├── external permissions
└── execution authority
```

This prevents a copied structure from inheriting claims that were only proven in another environment.

---

## 5. Truth is scope-local

Structure may be reused. Evidence must remain scoped to what it actually proves.

```text
LAB scope: API_GATEWAY = VERIFIED
                 │
                 │ schema may transfer
                 ▼
NEW scope: API_GATEWAY = UNKNOWN
```

A dynamic-scope library MUST NOT convert inherited structure into inherited proof.

Example guard:

```javascript
export function cloneForScope(source) {
  return {
    schema: structuredClone(source.schema),
    state: "UNKNOWN",
    evidence: []
  };
}
```

---

## 6. Identity and representation

Display text is not a sufficient machine identity.

```text
canonical_id
    ↓
machine_id
    ↓
display_name
    ↓
provider_representation
```

A provider may normalize punctuation, Unicode, filenames, URLs, or serialization. The canonical object must survive those differences.

Example:

```json
{
  "canonical_id": "os.public.001",
  "machine_id": "os_public_001",
  "display_name": "DrMarchand’s ∞ OS™"
}
```

The API SHOULD compare canonical identifiers for identity and SHOULD treat display names as presentation data.

---

## 7. Parent/child examples

The API pattern is intentionally generic.

### Private/public build scope

```text
DrMarchand’s OS™
├── DrMarchand’s ♾️ OS™
└── DrMarchand’s ∞ OS™
```

The shared parent does not make the two build scopes interchangeable.

### Finance scope

```text
Finance
├── Personal
└── Business
    ├── Laboratory context
    └── KEJ Studio context
```

A transaction can cross an explicit bridge without merging Personal and Business into one scope.

### Representation scope

```text
Canonical Object
├── Web representation
├── Print representation
└── Spreadsheet representation
```

Multiple representations may resolve back to one source object.

---

## 8. Bridge contract

Sibling scopes communicate through an explicit bridge rather than inheriting from one another.

```json
{
  "bridge_id": "bridge.personal.business",
  "source": "finance.personal",
  "target": "finance.business",
  "direction": "source_to_target",
  "payload_schema": "owner-funding.v1",
  "validation_rules": ["amount_positive", "source_recorded", "target_recorded"],
  "receipt_required": true
}
```

Reference interface:

```typescript
export interface ScopeBridge<T> {
  bridge_id: string;
  source: string;
  target: string;
  direction: "source_to_target" | "target_to_source" | "bidirectional";
  validate(payload: T): boolean;
  transfer(payload: T): Promise<BridgeReceipt>;
}
```

Communication does not create inheritance, ownership, or authority transfer by itself.

---

## 9. Promotion states

A useful lifecycle begins with explicit states rather than one overloaded `done` flag.

```text
DRAFT
  ↓
TESTED_LOCAL
  ↓
TESTED_REMOTE
  ↓
PACKAGED
  ↓
REVIEWED
  ↓
PUBLISHED
```

A generated artifact may be valid output without being approved or published.

```text
GENERATED ≠ VERIFIED ≠ APPROVED ≠ PUBLISHED
```

Libraries implementing promotion SHOULD require evidence for each transition and SHOULD preserve the previous state and transition receipt.

---

## 10. Generated artifacts

Dynamic scope can drive generators without making generated files the source of truth.

```text
canonical records
      ↓
resolved scope
      ↓
rules
      ↓
generator
      ↓
┌────────┬────────┬────────┐
▼        ▼        ▼        ▼
JSON     XLSX     PDF      HTML
```

Suggested manifest:

```json
{
  "object_id": "artifact.2026.001",
  "source_scope": "finance.business",
  "generator": "budget-report",
  "generator_version": "0.1.0",
  "ruleset": "finance.v1",
  "state": "GENERATED",
  "evidence": [],
  "human_gate": true
}
```

---

## 11. Proposed package surface

The first open-source implementation can stay deliberately small:

```text
src/
├── scope/
│   ├── resolve
│   ├── inherit
│   ├── validate
│   └── compare
├── bridge/
│   ├── define
│   ├── validate
│   └── receipt
├── state/
│   ├── transition
│   └── evidence
└── identity/
    ├── canonicalize
    └── represent
```

Potential language-neutral API:

```text
resolve(parent, child)
inherit(parent, child, policy)
compare(scope_a, scope_b)
validate(scope)
defineBridge(source, target, contract)
transition(object, next_state, evidence)
represent(object, provider)
```

---

## 12. First test suite

A true API library needs tests before expansion.

```javascript
it("inherits shared parent context", () => {});
it("preserves child-specific delta", () => {});
it("rejects an invalid parent edge", () => {});
it("does not inherit verification state", () => {});
it("does not merge siblings", () => {});
it("preserves canonical identity across representations", () => {});
it("requires an explicit bridge between siblings", () => {});
it("records evidence for promotion", () => {});
```

Unicode round-trip tests should also be first-class:

```javascript
const value = "DrMarchand’s ∞ OS™";
expect(decode(encode(value))).toBe(value);
```

---

## 13. Open-source boundary

This document describes a reusable software pattern. It does not grant authority to external callers, expose credentials, publish private system state, or make provider-specific truth portable across scopes.

Implementations should follow the repository's existing license and contribution rules. Provider adapters, storage drivers, database bindings, and framework integrations can be added as separate modules once the core behavior is proven.

---

## 14. Design law

```text
        ⟦ SHARE THE ROOT ⟧
                 +
        ⟦ PRESERVE THE Δ ⟧
                 =
          ⚙︎ DYNAMIC SCOPE
```

A dynamic system should not duplicate what two objects genuinely share, and it should not erase what makes them meaningfully different.

That is the first contract this library should make executable.
