---
name: 0.3.6-understand-no_happens_before_establishment
description: [0.3.6] A relaxed operation neither participates in nor establishes a happens-before relationship with any other opera
---

# understand-no_happens_before_establishment

**CALL NUMBER:** `deep_c11_memory_model.no_happens_before_establishment : concurrency_synchronization_primitives_and_memor(2)`
**DEFINITION:** A relaxed operation neither participates in nor establishes a happens-before relationship with any other operation; operations may be reordered arbitrarily across thread boundaries.

Invoke this skill to understand `no_happens_before_establishment` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `concurrency_synchronization_primitives_and_memor`
- **happens_before_relation** (d1): A fundamental ordering relation in memory models defining that if operation A happens-before operation B, then A's effects are visible to B; forms the basis for reasoning about program correctness in concurrent settings.
- **synchronizes_with** (d2): A relation between atomic operations in memory models where a release fence on one thread synchronizes with an acquire fence on another thread, establishing happens-before order across threads.

---
*Projected from the `concurrency synchronization primitives and memory models` KB (155 concepts / 137 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
