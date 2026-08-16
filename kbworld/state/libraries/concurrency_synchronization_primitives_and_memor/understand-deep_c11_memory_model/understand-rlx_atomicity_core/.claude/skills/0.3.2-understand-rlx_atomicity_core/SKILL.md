---
name: 0.3.2-understand-rlx_atomicity_core
description: [0.3.2] The fundamental indivisibility property that any relaxed atomic operation completes as a single non-interrupti
---

# understand-rlx_atomicity_core

**CALL NUMBER:** `deep_c11_memory_model.rlx_atomicity_core : concurrency_synchronization_primitives_and_memor(3)`
**DEFINITION:** The fundamental indivisibility property that any relaxed atomic operation completes as a single non-interruptible step with respect to the atomic variable; no observer can perceive partial state during the operation.

Invoke this skill to understand `rlx_atomicity_core` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `concurrency_synchronization_primitives_and_memor`
- **memory_order_relaxed** (d2): C11/C++11 memory ordering that only guarantees atomicity of the operation with no ordering constraints relative to other operations; allows all reorderings.
- **happens_before_relation** (d3): A fundamental ordering relation in memory models defining that if operation A happens-before operation B, then A's effects are visible to B; forms the basis for reasoning about program correctness in concurrent settings.
- **synchronizes_with** (d3): A relation between atomic operations in memory models where a release fence on one thread synchronizes with an acquire fence on another thread, establishing happens-before order across threads.

### from `deep_c11_memory_model`
- **rlx_atomic_read** (d1): A relaxed atomic load reads the atomic variable as one indivisible step; other threads cannot observe a torn or partial value from this read operation.
- **rlx_atomic_write** (d1): A relaxed atomic store writes the atomic variable as one indivisible step; other threads cannot observe a torn or partial value from this write operation.
- **rlx_lli_sc_provenance** (d1): Load-linked/store-conditional primitives or bus-snooping mechanisms provide the hardware-level indivisibility guarantee underlying software-level relaxed atomicity.
- **rlx_no_intermediate_state** (d1): The guarantee that no intermediate write value or partial read result is observable by any thread during the execution of a relaxed atomic operation; the variable transitions directly from old to new value.
- **rlx_per_variable_scope** (d1): The atomicity guarantee is scoped per individual atomic variable; relaxed atomicity on one variable does not impose or imply atomicity constraints on operations on any other variable.
- **rlx_rmw_indivisibility** (d1): Read-modify-write relaxed operations such as fetch_add, fetch_sub, and compare_exchange_strong complete atomically as a single indivisible transaction on the atomic variable.
- **rlx_vs_ordering_distinct** (d1): The distinction that atomicity and ordering are orthogonal properties; relaxed operations maintain atomicity but impose zero ordering constraints relative to other operations on any variable.
- **rlx_cas_atomicity** (d2): The compare-and-exchange relaxed operation atomically reads the current value, compares with expected, and conditionally writes the desired value as one indivisible step if the comparison succeeds.
- **memory_order_relaxed_atomicity_guarantee** (d3): The indivisibility guarantee that a relaxed atomic operation completes as a single indivisible step; no intermediate state is observable by other threads during the operation, scoped to the specific atomic variable being read or written.
- **memory_order_relaxed_coherence_per_location** (d3): The property that each atomic variable maintains its own independent coherence order but this order is not coordinated with coherence orders of other variables; operations on separate variables are totally unordered with respect to each other.
- **memory_order_relaxed_load_value_visibility** (d3): The undefined timing of when a relaxed load obtains its value; a load may observe any value from the modification order up to that point, with no guarantee about when the load's value becomes visible to other threads.
- **memory_order_relaxed_modification_order** (d3): The per-variable constraint that each atomic variable still has a well-defined modification order agreed upon by all threads, even though relaxed operations on different variables are unconstrained relative to each other.
- **memory_order_relaxed_no_ordering_constraints** (d3): The defining property that relaxed operations impose zero ordering constraints relative to any other operations on any memory location; no happens-before or synchronizes-with relationship is established with respect to other threads.
- **memory_order_relaxed_no_synchronization** (d3): The absence of any synchronization relationship; relaxed operations do not participate in the synchronizes-with relation and do not establish happens-before edges across thread boundaries regardless of visibility.
- **memory_order_relaxed_program_order_within_thread** (d3): The within-thread ordering guarantee that within a single thread, the program order of relaxed operations is still preserved for that thread's own perspective; only cross-thread visibility and cross-variable ordering are relaxed.
- **memory_order_relaxed_reordering_freedom** (d3): The freedom to reorder relaxed operations across variable boundaries; a relaxed store may be reordered with respect to a relaxed load on a different variable, and loads may observe values in an order inconsistent with program order across different locations.
- **memory_order_relaxed_store_buffering** (d3): The phenomenon that relaxed stores may be buffered in store buffers and become visible to other threads in an order different from the program order of the storing thread.

---
*Projected from the `concurrency synchronization primitives and memory models` KB (277 concepts / 278 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
