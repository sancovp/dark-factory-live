# understand-sequentially_consistent

**CALL NUMBER:** `concurrency_synchronization_primitives_and_memor.sequentially_consistent : deep_c11_memory_model(10)`
**DEFINITION:** The strongest memory ordering requiring a single total order of all sequentially consistent operations visible to all threads; implied by default for std::atomic operations in C++.

Invoke this skill to understand `sequentially_consistent` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `concurrency_synchronization_primitives_and_memor`
- **happens_before_relation** (d2): A fundamental ordering relation in memory models defining that if operation A happens-before operation B, then A's effects are visible to B; forms the basis for reasoning about program correctness in concurrent settings.
- **synchronizes_with** (d2): A relation between atomic operations in memory models where a release fence on one thread synchronizes with an acquire fence on another thread, establishing happens-before order across threads.

### from `deep_c11_memory_model`
- **memory_order_relaxed_vs_seq_cst** (d1): The ordering contrast where sequentially_consistent imposes a single global total order visible to all threads, while memory_order_relaxed has no global ordering requirement across variables.
- **seq_cst_atomic_visibility** (d1): The guarantee that all threads observe the effects of a sequentially consistent operation at the same logical point in the global total order; reads observe the most recent write in the total order.
- **seq_cst_default_atomic_ordering** (d1): The default memory ordering for std::atomic operations in C11/C++11 when no memory_order is explicitly specified; provides the strongest guarantees without requiring explicit fence code.
- **seq_cst_fence** (d1): The explicit memory fence with sequentially consistent ordering that provides both acquire and release semantics plus additional ordering constraints to enforce the global total order.
- **seq_cst_global_total_order** (d1): A single total order of all sequentially consistent operations that is visible and agreed upon by all threads in the system; the interleaving point where all threads observe the same sequence of operations.
- **seq_cst_implies_acquire** (d1): A load operation with sequentially consistent ordering carries acquire semantics; all subsequent loads and stores cannot be reordered before the seq_cst load.
- **seq_cst_implies_release** (d1): A store operation with sequentially consistent ordering carries release semantics; all prior loads and stores cannot be reordered after the seq_cst store.
- **seq_cst_indivisible_atomicity** (d1): The property that each sequentially consistent operation appears indivisible and instantaneous to all observers; no intermediate states are visible during the operation.
- **seq_cst_program_order_preservation** (d1): Within each thread, sequentially consistent operations maintain program order; no reordering of these operations is permitted within the same thread.
- **seq_cst_synchronization_protocol** (d1): The protocol by which sequentially consistent operations establish synchronization points between threads; creates a happens-before relationship across thread boundaries.

## CONSUMERS (what needs this)
`c11_memory_model`, `load_buffering_allowed`, `modification_order_coherence`, `relaxed_vs_seq_cst`, `seq_cst_atomic_visibility_all_threads_agree_on_visibility_sequence`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (211 concepts / 207 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*