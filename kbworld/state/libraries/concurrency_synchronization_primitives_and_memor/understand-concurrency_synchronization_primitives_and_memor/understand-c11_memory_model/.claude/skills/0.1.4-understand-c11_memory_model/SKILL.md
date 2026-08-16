---
name: 0.1.4-understand-c11_memory_model
description: [0.1.4] Standard C11 specification defining memory orderings: memory_order_relaxed, memory_order_consume, memory_order
---

# understand-c11_memory_model

**CALL NUMBER:** `concurrency_synchronization_primitives_and_memor.c11_memory_model : deep_c11_memory_model(29)`
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
- **memory_order_relaxed_vs_acquire** (d2): The ordering contrast where acquire_semantics prevents subsequent operations from being reordered before the acquire, while memory_order_relaxed permits all such reorderings with no barrier effect.
- **memory_order_relaxed_atomicity_guarantee** (d2): The indivisibility guarantee that a relaxed atomic operation completes as a single indivisible step; no intermediate state is observable by other threads during the operation, scoped to the specific atomic variable being read or written.
- **memory_order_relaxed_coherence_per_location** (d2): The property that each atomic variable maintains its own independent coherence order but this order is not coordinated with coherence orders of other variables; operations on separate variables are totally unordered with respect to each other.
- **memory_order_relaxed_load_value_visibility** (d2): The undefined timing of when a relaxed load obtains its value; a load may observe any value from the modification order up to that point, with no guarantee about when the load's value becomes visible to other threads.
- **memory_order_relaxed_modification_order** (d2): The per-variable constraint that each atomic variable still has a well-defined modification order agreed upon by all threads, even though relaxed operations on different variables are unconstrained relative to each other.
- **memory_order_relaxed_no_ordering_constraints** (d2): The defining property that relaxed operations impose zero ordering constraints relative to any other operations on any memory location; no happens-before or synchronizes-with relationship is established with respect to other threads.
- **memory_order_relaxed_no_synchronization** (d2): The absence of any synchronization relationship; relaxed operations do not participate in the synchronizes-with relation and do not establish happens-before edges across thread boundaries regardless of visibility.
- **memory_order_relaxed_program_order_within_thread** (d2): The within-thread ordering guarantee that within a single thread, the program order of relaxed operations is still preserved for that thread's own perspective; only cross-thread visibility and cross-variable ordering are relaxed.
- **memory_order_relaxed_reordering_freedom** (d2): The freedom to reorder relaxed operations across variable boundaries; a relaxed store may be reordered with respect to a relaxed load on a different variable, and loads may observe values in an order inconsistent with program order across different locations.
- **memory_order_relaxed_store_buffering** (d2): The phenomenon that relaxed stores may be buffered in store buffers and become visible to other threads in an order different from the program order of the storing thread.
- **memory_order_relaxed_vs_release** (d2): The ordering contrast where release_semantics prevents prior operations from being reordered after the release, while memory_order_relaxed permits all such reorderings with no barrier effect.
- **memory_order_relaxed_vs_seq_cst** (d2): The ordering contrast where sequentially_consistent imposes a single global total order visible to all threads, while memory_order_relaxed has no global ordering requirement across variables.
- **seq_cst_atomic_visibility** (d2): The guarantee that all threads observe the effects of a sequentially consistent operation at the same logical point in the global total order; reads observe the most recent write in the total order.
- **seq_cst_default_atomic_ordering** (d2): The default memory ordering for std::atomic operations in C11/C++11 when no memory_order is explicitly specified; provides the strongest guarantees without requiring explicit fence code.
- **seq_cst_fence** (d2): The explicit memory fence with sequentially consistent ordering that provides both acquire and release semantics plus additional ordering constraints to enforce the global total order.
- **seq_cst_global_total_order** (d2): A single total order of all sequentially consistent operations that is visible and agreed upon by all threads in the system; the interleaving point where all threads observe the same sequence of operations.
- **seq_cst_implies_acquire** (d2): A load operation with sequentially consistent ordering carries acquire semantics; all subsequent loads and stores cannot be reordered before the seq_cst load.
- **seq_cst_implies_release** (d2): A store operation with sequentially consistent ordering carries release semantics; all prior loads and stores cannot be reordered after the seq_cst store.
- **seq_cst_indivisible_atomicity** (d2): The property that each sequentially consistent operation appears indivisible and instantaneous to all observers; no intermediate states are visible during the operation.
- **seq_cst_program_order_preservation** (d2): Within each thread, sequentially consistent operations maintain program order; no reordering of these operations is permitted within the same thread.
- **seq_cst_synchronization_protocol** (d2): The protocol by which sequentially consistent operations establish synchronization points between threads; creates a happens-before relationship across thread boundaries.
- **relaxed_coherence_per_location_vs_acquire_global_observation** (d3): The observation model contrast where relaxed operations on different variables maintain independent per-variable coherence orders with no cross-variable ordering coordination, while acquire semantics participates in the global sequentially consistent order when mixed with seq_cst operations.
- **relaxed_load_value_visibility_timing_vs_acquire_visibility_timing** (d3): The visibility timing contrast where a relaxed load may observe any value from the modification order at an undefined time with no guarantee about when the value becomes visible to other threads, while an acquire load observes the value at a specific point in the happens-before order with guaranteed visibility semantics.
- **relaxed_no_happens_before_edge_vs_acquire_hb_edge** (d3): The ordering contrast where relaxed operations never establish a happens-before edge with operations on other threads regardless of visibility timing, while acquire semantics combined with release on another thread creates a transitive happens-before edge connecting the release writer to the acquire reader.
- **relaxed_no_ordering_constraints_vs_acquire_subsequent_constrained** (d3): The scope contrast where relaxed operations impose zero ordering constraints on any other operations on any memory location, while acquire semantics constrains all subsequent loads and stores in the same thread to remain after the acquire in program order.

## CONSUMERS (what needs this)
`c11_atomic_thread_fence_contrast`, `cpp11_memory_model`, `data_race`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (277 concepts / 278 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
