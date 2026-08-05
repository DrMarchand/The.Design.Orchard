# GitHub Brand Consistency Policy v0.1

Status: PROPOSED
Authority: © Design Orchard LLC
Scope: Connected GitHub accounts, organizations, repositories, paths, documentation headers, package identifiers, workflow labels, and deployment references.

## Governing principle

Canonical display identities and technical GitHub identifiers are related but not interchangeable.

A repository slug may use an ASCII-safe technical form when GitHub or tooling constraints make the canonical display form impractical. Every technical slug must be explicitly mapped to one canonical identity, purpose, owner, authority, visibility, and lifecycle state.

## Locked display identities

- © Design Orchard LLC
- 🌴 Design Orchard™
- 🔬 DrMarchand’s Lab⚛︎ratory™
- 📚 DrMarchand’s ⚛︎ Library™
- DrMarchand’s ⚙︎ Nɛuro-Forge Engine™
- DrMarchand’s OS™ — parent operating-system identity
- DrMarchand’s ♾️ OS™ — INFINITY component
- DrMarchand’s ∞ OS™ — INFINITE component
- DrMarchand’s ⚛︎ Atlas
- 🪬 Big Brother

## DrMarchand’s OS™ hierarchy law

DrMarchand’s OS™ is the parent operating-system identity.

```text
DrMarchand’s OS™
├── DrMarchand’s ♾️ OS™ — INFINITY
└── DrMarchand’s ∞ OS™ — INFINITE
```

DrMarchand’s ♾️ OS™ and DrMarchand’s ∞ OS™ are separate canonical components of DrMarchand’s OS™.

- `♾️` maps to **INFINITY**.
- `∞` maps to **INFINITE**.
- Neither component may be represented as the complete parent operating system by itself.
- The components must not be treated as spelling or symbol variants of one another.
- Parent-child relationships must be registered explicitly in Atlas and in the GitHub repository registry.
- A technical repository may represent the parent, one component, or a shared implementation surface, but that mapping must be declared rather than inferred.

## Prohibited drift

- `DrMarchand’s Infinity OS™` used in place of the exact canonical identity `DrMarchand’s ♾️ OS™`
- `DrMarchand’s Infinite OS™` used in place of the exact canonical identity `DrMarchand’s ∞ OS™`
- treating `DrMarchand’s OS™`, `DrMarchand’s ♾️ OS™`, and `DrMarchand’s ∞ OS™` as interchangeable names
- treating either component as the entire parent identity without an explicit scoped context
- `♾️ DrMarchand’s ♾️ OS™`
- `∞ DrMarchand’s ∞ OS™`
- `☸︎ DrMarchand’s Nɛuro-Forge Engine™`
- `⚙︎ DrMarchand’s Nɛuro-Forge Engine™`
- `DrMarchand’s Nɛuro-Forge Engine™` when the locked external identity is required
- `Neuro-Forge` substituted for `Nɛuro-Forge` in canonical display text
- repository or organization names treated as canonical identities without an approved mapping

## Technical naming rules

1. Repository slugs must be ASCII-safe and stable.
2. Canonical display names belong in repository descriptions, README titles, governance files, release manifests, and user-facing interfaces.
3. Domain repositories may use the exact lowercase domain as the technical slug.
4. Infrastructure repositories may use registered abbreviations such as `nfe`, but the abbreviation must be listed in the registry.
5. Forks, mirrors, vendor sources, experiments, and personal repositories must be explicitly classified.
6. Renames, transfers, archives, and visibility changes require migration impact review, redirect validation, and rollback planning.
7. Historical filenames may remain unchanged when renaming would damage references, but their status must be documented and their content must use canonical display identities.
8. Symbols are semantic identifiers, not decoration. Symbol substitutions require authority review.
9. `DrMarchand-OS`, `infinity-os`, `infinite-os`, and similar slugs must declare whether they map to the parent, the INFINITY component, the INFINITE component, or a shared implementation surface.
10. A shared implementation repository must not erase the separate canonical identities or their parent-child relationships.

## Required repository metadata

Every governed repository must define:

- repository ID
- full name
- technical slug
- canonical entity mapping
- parent identity
- component relationship
- purpose
- owner account or organization
- authority role
- visibility
- default branch
- lifecycle state
- classification
- canonical README title
- deployment relationship
- evidence reference
- exceptions

## Classification values

- CORE
- SUPPORTING
- WEBSITE
- INFRASTRUCTURE
- GOVERNANCE
- EXPERIMENT
- FORK_OR_VENDOR
- PERSONAL
- HISTORICAL
- SUPERSEDED
- UNRESOLVED

## Validation checklist

- Repository full name is registered.
- Repository description uses the approved display identity.
- README title uses the approved display identity.
- Parent versus component mapping is explicit.
- INFINITY versus INFINITE mapping is explicit.
- Paths do not create an unregistered competing identity.
- Package names and namespaces are mapped.
- GitHub topics are aligned.
- Workflow names are aligned.
- Deployment manifests reference the correct repository and entity.
- Visibility matches the data classification.
- Default branch is documented.
- Fork, vendor, personal, or experimental status is disclosed.
- Evidence and exception references are attached.

## Change control

This policy remains PROPOSED until reviewed through the pull request, reconciled with Atlas identity records, and acknowledged by the human authority. No repository rename or transfer is authorized by this document alone.
