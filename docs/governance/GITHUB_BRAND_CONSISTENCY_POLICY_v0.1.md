# GitHub Brand Consistency Policy v0.1

Status: PROPOSED
Authority: © Design Orchard LLC
Scope: Connected GitHub accounts, organizations, repositories, paths, documentation headers, package identifiers, workflow labels, and deployment references.

## Governing principle

Canonical display identities and technical GitHub identifiers are related but not interchangeable.

A repository slug may use an ASCII-safe technical form when GitHub or tooling constraints make the canonical display form impractical. Every technical slug must be explicitly mapped to one canonical identity, purpose, owner, authority, visibility, lifecycle state, and relationship type.

## Locked display identities

- © Design Orchard LLC
- 🏝️ Design Orchard℠
- 🌴 Design Orchard™
- 🔬 DrMarchand’s Lab⚛︎ratory™
- 📚 DrMarchand’s ⚛︎ Library™
- DrMarchand’s ⚙︎ Nɛuro-Forge Engine™
- DrMarchand’s OS™ — parent operating-system identity
- DrMarchand’s 🗺️ OS™ — core operating-system layer that holds Atlas
- DrMarchand’s 🔬 OS™ — Laboratory link component
- DrMarchand’s 📚 OS™ — Library link component
- DrMarchand’s 🏝️ OS™ — ecosystem link component
- DrMarchand’s 🌴 OS™ — environment link component
- DrMarchand’s ♾️ OS™ — INFINITY component
- DrMarchand’s ∞ OS™ — INFINITE component
- DrMarchand’s ⚛︎ Atlas — identity and relationship registry held within DrMarchand’s 🗺️ OS™
- 🪬 Big Brother

## DrMarchand’s OS™ hierarchy and link law

DrMarchand’s OS™ is the parent operating-system identity.

```text
DrMarchand’s OS™
├── DrMarchand’s 🗺️ OS™ — core
│   └── holds DrMarchand’s ⚛︎ Atlas
├── DrMarchand’s 🔬 OS™
│   └── links to 🔬 DrMarchand’s Lab⚛︎ratory™
├── DrMarchand’s 📚 OS™
│   └── links to 📚 DrMarchand’s ⚛︎ Library™
├── DrMarchand’s 🏝️ OS™
│   └── links to the ecosystem and 🏝️ Design Orchard℠
├── DrMarchand’s 🌴 OS™
│   └── links to an environment and 🌴 Design Orchard™
├── DrMarchand’s ♾️ OS™ — INFINITY
└── DrMarchand’s ∞ OS™ — INFINITE
```

### Core containment

DrMarchand’s 🗺️ OS™ is the core operating-system layer that holds and supports DrMarchand’s ⚛︎ Atlas.

- Atlas remains a distinct canonical component.
- Atlas is contained within the core; it is not synonymous with the core.
- Atlas resolves canonical identity, scope, relationships, dependencies, classifications, and state.
- Atlas does not inherit execution authority from its containment within the core.
- DrMarchand’s ⚙︎ Nɛuro-Forge Engine™ remains the execution authority.

### Link components

The symbol-specific OS components are governed links or interfaces. They do not absorb, replace, or become identical to the linked domain.

- DrMarchand’s 🔬 OS™ links DrMarchand’s OS™ to 🔬 DrMarchand’s Lab⚛︎ratory™.
- DrMarchand’s 📚 OS™ links DrMarchand’s OS™ to 📚 DrMarchand’s ⚛︎ Library™.
- DrMarchand’s 🏝️ OS™ links DrMarchand’s OS™ to the broader ecosystem and 🏝️ Design Orchard℠.
- DrMarchand’s 🌴 OS™ links DrMarchand’s OS™ to an environment and 🌴 Design Orchard™.

The terms `ecosystem` and `environment` are separate relationship classes and must not be silently interchanged.

### Infinity and Infinite components

DrMarchand’s ♾️ OS™ and DrMarchand’s ∞ OS™ are separate canonical components of DrMarchand’s OS™.

- `♾️` maps to **INFINITY**.
- `∞` maps to **INFINITE**.
- Neither component may be represented as the complete parent operating system by itself.
- The components must not be treated as spelling or symbol variants of one another.

## Prohibited drift

- treating DrMarchand’s 🗺️ OS™ and DrMarchand’s ⚛︎ Atlas as the same object
- treating an OS link component and its linked institution, ecosystem, environment, or brand identity as the same object
- treating `links_to`, `contains`, `holds`, `belongs_to`, and `executes_for` as interchangeable relationships
- assigning Laboratory authority to DrMarchand’s 🔬 OS™ merely because it links to the Laboratory
- assigning Library custody authority to DrMarchand’s 📚 OS™ merely because it links to the Library
- collapsing 🏝️ Design Orchard℠ and 🌴 Design Orchard™ into one identity
- collapsing ecosystem and environment into one scope
- `DrMarchand’s Infinity OS™` used in place of `DrMarchand’s ♾️ OS™`
- `DrMarchand’s Infinite OS™` used in place of `DrMarchand’s ∞ OS™`
- treating any DrMarchand’s OS™ component as the entire parent identity without an explicit scoped context
- `☸︎ DrMarchand’s Nɛuro-Forge Engine™`
- `⚙︎ DrMarchand’s Nɛuro-Forge Engine™`
- `Neuro-Forge` substituted for `Nɛuro-Forge` in canonical display text
- repository or organization names treated as canonical identities without an approved mapping

## Technical naming rules

1. Repository slugs must be ASCII-safe and stable.
2. Canonical display names belong in repository descriptions, README titles, governance files, release manifests, and user-facing interfaces.
3. Domain repositories may use the exact lowercase domain as the technical slug.
4. Infrastructure repositories may use registered abbreviations, but each abbreviation must be listed in the registry.
5. Forks, mirrors, vendor sources, experiments, and personal repositories must be explicitly classified.
6. Renames, transfers, archives, and visibility changes require migration-impact review, redirect validation, and rollback planning.
7. Historical filenames may remain unchanged when renaming would damage references, but their status must be documented and their content must use canonical display identities.
8. Symbols are semantic identifiers, not decoration. Symbol substitutions require authority review.
9. Technical slugs must declare whether they map to the parent, the core, Atlas, a link component, INFINITY, INFINITE, or a shared implementation surface.
10. Shared implementation repositories must not erase separate canonical identities, containment relationships, link relationships, or authority boundaries.

## Required repository metadata

Every governed repository must define:

- repository ID
- full name
- technical slug
- canonical entity mapping
- parent identity
- relationship type
- relationship target
- containment relationship
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

## Relationship values

- CONTAINS
- HOLDS
- LINKS_TO
- INTERFACES_WITH
- EXECUTES_FOR
- OBSERVES
- PRESERVES
- PRESENTS
- SHARED_IMPLEMENTATION_SURFACE
- UNRESOLVED

## Classification values

- CORE
- LINK_COMPONENT
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
- Parent, core, containment, component, and link mappings are explicit.
- Atlas is mapped as held within DrMarchand’s 🗺️ OS™ without execution-authority drift.
- Each OS link component has one registered relationship target and relationship class.
- The linked identity remains distinct from the OS component.
- Ecosystem and environment scopes remain distinct.
- 🏝️ Design Orchard℠ and 🌴 Design Orchard™ remain distinct.
- INFINITY versus INFINITE mapping is explicit.
- Paths do not create an unregistered competing identity.
- Package names and namespaces are mapped.
- GitHub topics and workflow names are aligned.
- Deployment manifests reference the correct repository and entity.
- Visibility matches the data classification.
- Default branch is documented.
- Fork, vendor, personal, or experimental status is disclosed.
- Evidence and exception references are attached.

## Change control

This policy remains PROPOSED until reviewed through the pull request, reconciled with Atlas identity records, and acknowledged by the human authority. No repository rename, transfer, archive, or visibility change is authorized by this document alone.
