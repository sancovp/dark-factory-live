# understand-c11_memory_model

**CALL NUMBER:** `concurrency_synchronization_primitives_and_memor.c11_memory_model : deep_c11_memory_model(9)`
**DEFINITION:** Standard C11 specification defining memory orderings: memory_order_relaxed, memory_order_consume, memory_order_acquire, memory_order_release, memory_order_acq_rel, memory_order_seq_cst; defines happens-before and synchronizes-with relations.

Invoke this skill to understand `c11_memory_model` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `concurrency_synchronization_primitives_and_memor`
- **acquire_semantics** (d1): Memory ordering semantics ensuring all subsequent loads/stores cannot be reordered before the acquire operation; used for lock acquisition, reading a flag after volatile write.
- **happens_before_relation** (d1): A fundamental ordering relation in memory models defining that if operation A happens-before operation B, then A's effects are visible to B; forms the basis for reasoning about program correctness in concurrent settings.
- **memory_order_relaxed** (d1): C11/C++11 memory ordering that only guarantees atomicity of the operation with no ordering constraints relative to other operations; allows all reorderings.
- **release_semantics** (d1): Memory ordering semantics ensuring all prior loads/stores cannot be reordered after the release operation; used for lock release, writing data before a volatile flag.
- **sequentially_consistent** (d1): The strongest memory ordering requiring a single total order of all sequentially consistent operations visible to all threads; implied by default for std::atomic operations in C++.
- **synchronizes_with** (d2): A relation between atomic operations in memory models where a release fence on one thread synchronizes with an acquire fence on another thread, establishing happens-before order across threads.

### from `deep_c11_memory_model`
- **seq_cst_atomic_visibility** (d2): The guarantee that all threads observe the effects of a sequentially consistent operation at the same logical point in the global total order; reads observe the most recent write in the total order.
- **seq_cst_default_atomic_ordering** (d2): The default memory ordering for std::atomic operations in C11/C++11 when no memory_order is explicitly specified; provides the strongest guarantees without requiring explicit fence code.
- **seq_cst_fence** (d2): The explicit memory fence with sequentially consistent ordering that provides both acquire and release semantics plus additional ordering constraints to enforce the global total order.
- **seq_cst_global_total_order** (d2): A single total order of all sequentially consistent operations that is visible and agreed upon by all threads in the system; the interleaving point where all threads observe the same sequence of operations.
- **seq_cst_implies_acquire** (d2): A load operation with sequentially consistent ordering carries acquire semantics; all subsequent loads and stores cannot be reordered before the seq_cst load.
- **seq_cst_implies_release** (d2): A store operation with sequentially consistent ordering carries release semantics; all prior loads and stores cannot be reordered after the seq_cst store.
- **seq_cst_indivisible_atomicity** (d2): The property that each sequentially consistent operation appears indivisible and instantaneous to all observers; no intermediate states are visible during the operation.
- **seq_cst_program_order_preservation** (d2): Within each thread, sequentially consistent operations maintain program order; no reordering of these operations is permitted within the same thread.
- **seq_cst_synchronization_protocol** (d2): The protocol by which sequentially consistent operations establish synchronization points between threads; creates a happens-before relationship across thread boundaries.

## CONSUMERS (what needs this)
`c11_atomic_thread_fence_contrast`, `cpp11_memory_model`, `data_race`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (155 concepts / 137 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*