---
name: 0.1.3-understand-happens_before_relation
description: "[0.1.3] A fundamental ordering relation in memory models defining that if operation A happens-before operation B, then"
---

# understand-happens_before_relation

**CALL NUMBER:** `concurrency_synchronization_primitives_and_memor.happens_before_relation`
**DEFINITION:** A fundamental ordering relation in memory models defining that if operation A happens-before operation B, then A's effects are visible to B; forms the basis for reasoning about program correctness in concurrent settings.

Invoke this skill to understand `happens_before_relation` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `concurrency_synchronization_primitives_and_memor`
- **synchronizes_with** (d1): A relation between atomic operations in memory models where a release fence on one thread synchronizes with an acquire fence on another thread, establishing happens-before order across threads.

## CONSUMERS (what needs this)
`c11_memory_model`, `memory_order_relaxed`, `no_happens_before_establishment`, `relaxed_no_happens_before_edge_vs_acquire_hb_edge`, `seq_cst_atomic_visibility_happens_before_cutoff_visibility`, `seq_cst_atomic_visibility_observation_consistency_rule`, `seq_cst_global_total_order`, `synchronizes_with_absence`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (277 concepts / 278 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
