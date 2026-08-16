---
name: 0.3.3-understand-seq_cst_global_total_order
description: [0.3.3] A single total order of all sequentially consistent operations that is visible and agreed upon by all threads 
---

# understand-seq_cst_global_total_order

**CALL NUMBER:** `deep_c11_memory_model.seq_cst_global_total_order : concurrency_synchronization_primitives_and_memor(2)`
**DEFINITION:** A single total order of all sequentially consistent operations that is visible and agreed upon by all threads in the system; the interleaving point where all threads observe the same sequence of operations.

Invoke this skill to understand `seq_cst_global_total_order` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `concurrency_synchronization_primitives_and_memor`
- **happens_before_relation** (d1): A fundamental ordering relation in memory models defining that if operation A happens-before operation B, then A's effects are visible to B; forms the basis for reasoning about program correctness in concurrent settings.
- **synchronizes_with** (d2): A relation between atomic operations in memory models where a release fence on one thread synchronizes with an acquire fence on another thread, establishing happens-before order across threads.

## CONSUMERS (what needs this)
`seq_cst_atomic_visibility_all_threads_agree_on_visibility_sequence`, `seq_cst_atomic_visibility_most_recent_write_in_total_order`, `seq_cst_atomic_visibility_total_order_observation_point`, `sequentially_consistent`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (277 concepts / 278 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
