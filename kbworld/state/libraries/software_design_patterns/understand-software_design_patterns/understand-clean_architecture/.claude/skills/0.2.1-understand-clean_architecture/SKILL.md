---
name: 0.2.1-understand-clean_architecture
description: [0.2.1] Layered architecture with independent frameworks and clear dependency rules pointing inward.
---

# understand-clean_architecture

**CALL NUMBER:** `software_design_patterns.clean_architecture`
**DEFINITION:** Layered architecture with independent frameworks and clear dependency rules pointing inward.

Invoke this skill to understand `clean_architecture` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `software_design_patterns`
- **hexagonal_architecture_pattern** (d1): Ports_and_adapters architecture that separates core business logic from external concerns, with ports defining interfaces and adapters implementing them.

## CONSUMERS (what needs this)
`clean_architecture_pattern`

---
*Projected from the `software design patterns` KB (211 concepts / 36 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
