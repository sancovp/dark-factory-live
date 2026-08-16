---
name: 0.3.4-understand-rlx_atomicity_core
description: "[0.3.4] The fundamental indivisibility property that any relaxed atomic operation completes as a single non-interrupti"
---

# understand-rlx_atomicity_core

**CALL NUMBER:** `deep_c11_memory_model.rlx_atomicity_core : deep_synchronizes_with(20), deep_happens_before_relat(7), concurrency_synchronization_primitives_and_memor(5)`
**DEFINITION:** The fundamental indivisibility property that any relaxed atomic operation completes as a single non-interruptible step with respect to the atomic variable; no observer can perceive partial state during the operation.

Invoke this skill to understand `rlx_atomicity_core` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **atomic_cas** (d5): Compare-and-swap operation atomically loading a value, comparing it to an expected value, and storing a new value only if they matched, returning whether the swap occurred.

### from `concurrency_synchronization_primitives_and_memor`
- **memory_order_relaxed** (d2): C11/C++11 memory ordering that only guarantees atomicity of the operation with no ordering constraints relative to other operations; allows all reorderings.
- **happens_before_relation** (d3): A fundamental ordering relation in memory models defining that if operation A happens-before operation B, then A's effects are visible to B; forms the basis for reasoning about program correctness in concurrent settings.
- **synchronizes_with** (d3): A relation between atomic operations in memory models where a release fence on one thread synchronizes with an acquire fence on another thread, establishing happens-before order across threads.
- **atomic_compare_exchange** (d4): C++11/C11 atomic operation attempting to replace expected value with desired; returns boolean indicating success; on failure, expected is updated with actual value for retry loops.
- **acquire_semantics** (d5): Memory ordering semantics ensuring all subsequent loads/stores cannot be reordered before the acquire operation; used for lock acquisition, reading a flag after volatile write.

### from `deep_c11_memory_model`
- **rlx_atomic_read** (d1): A relaxed atomic load reads the atomic variable as one indivisible step; other threads cannot observe a torn or partial value from this read operation.
- **rlx_atomic_write** (d1): A relaxed atomic store writes the atomic variable as one indivisible step; other threads cannot observe a torn or partial value from this write operation.
- **rlx_lli_sc_provenance** (d1): Load-linked/store-conditional primitives or bus-snooping mechanisms provide the hardware-level indivisibility guarantee underlying software-level relaxed atomicity.
- **rlx_no_intermediate_state** (d1): The guarantee that no intermediate write value or partial read result is observable by any thread during the execution of a relaxed atomic operation; the variable transitions directly from old to new value.
- **rlx_per_variable_scope** (d1): The atomicity guarantee is scoped per individual atomic variable; relaxed atomicity on one variable does not impose or imply atomicity constraints on operations on any other variable.
- **rlx_rmw_indivisibility** (d1): Read-modify-write relaxed operations such as fetch_add, fetch_sub, and compare_exchange_strong complete atomically as a single indivisible transaction on the atomic variable.
- **rlx_vs_ordering_distinct** (d1): The distinction that atomicity and ordering are orthogonal properties; relaxed operations maintain atomicity but impose zero ordering constraints relative to other operations on any variable.
- **rlx_cas_atomicity** (d2): The compare-and-exchange relaxed operation atomically reads the current value, compares with expected, and conditionally writes the desired value as one indivisible step if the comparison succeeds.
- **indivisibility_property** (d3): The fundamental property that a relaxed atomic operation executes as a single indivisible step from the perspective of all threads; the operation either completes fully or not at all without observable intermediate states.
- **memory_order_relaxed_atomicity_guarantee** (d3): The indivisibility guarantee that a relaxed atomic operation completes as a single indivisible step; no intermediate state is observable by other threads during the operation, scoped to the specific atomic variable being read or written.
- **memory_order_relaxed_coherence_per_location** (d3): The property that each atomic variable maintains its own independent coherence order but this order is not coordinated with coherence orders of other variables; operations on separate variables are totally unordered with respect to each other.
- **memory_order_relaxed_load_value_visibility** (d3): The undefined timing of when a relaxed load obtains its value; a load may observe any value from the modification order up to that point, with no guarantee about when the load's value becomes visible to other threads.
- **memory_order_relaxed_modification_order** (d3): The per-variable constraint that each atomic variable still has a well-defined modification order agreed upon by all threads, even though relaxed operations on different variables are unconstrained relative to each other.
- **memory_order_relaxed_no_ordering_constraints** (d3): The defining property that relaxed operations impose zero ordering constraints relative to any other operations on any memory location; no happens-before or synchronizes-with relationship is established with respect to other threads.
- **memory_order_relaxed_no_synchronization** (d3): The absence of any synchronization relationship; relaxed operations do not participate in the synchronizes-with relation and do not establish happens-before edges across thread boundaries regardless of visibility.
- **memory_order_relaxed_program_order_within_thread** (d3): The within-thread ordering guarantee that within a single thread, the program order of relaxed operations is still preserved for that thread's own perspective; only cross-thread visibility and cross-variable ordering are relaxed.
- **memory_order_relaxed_reordering_freedom** (d3): The freedom to reorder relaxed operations across variable boundaries; a relaxed store may be reordered with respect to a relaxed load on a different variable, and loads may observe values in an order inconsistent with program order across different locations.
- **memory_order_relaxed_store_buffering** (d3): The phenomenon that relaxed stores may be buffered in store buffers and become visible to other threads in an order different from the program order of the storing thread.
- **no_tearing_guarantee** (d3): The guarantee that multi-byte atomic values cannot be observed in a torn state where some bytes reflect the old value and others reflect a new concurrent value.
- **relaxed_mod_order_def** (d3): The well-defined sequential order of all store operations to a single atomic variable; every relaxed store to variable x appends to x's modification order in some position, and all threads agree on this order for x.
- **intermediate_state_invisibility** (d4): The guarantee that no thread can observe a partially completed relaxed atomic operation; all threads observe either the state before or after the operation, never during its execution.
- **load_indivisibility** (d4): A relaxed atomic load returns exactly one value from the modification order of the target variable; no torn read of a partial value encoded in fewer bits than the atomic word is possible.
- **no_partial_observation** (d4): The constraint that observers of a relaxed atomic operation cannot see byte-level or word-level fragments of the operation in flight; only complete before or after states are visible.
- **read_modify_write_indivisibility** (d4): The indivisibility of compound read-modify-write operations under relaxed ordering; fetch_add fetch_sub and similar operations complete atomically without observable intermediate states.
- **store_indivisibility** (d4): A relaxed atomic store writes the complete value as one indivisible step; no intermediate write of a partial value encoded in fewer bits than the atomic word is observable by any thread.

### from `deep_happens_before_relat`
- **acquire_fence** (d5): A memory ordering primitive that ensures all load and store operations appearing after the fence in program order do not begin until the fence completes and all prior writes are visible.
- **release_fence** (d5): A memory ordering primitive that ensures all load and store operations appearing before the fence in program order complete before any operations appearing after the fence begin.
- **synchronizes_with_acquire_side** (d6): The acquire-side endpoint of a synchronizes_with relation: an atomic operation or fence that performs an acquire action, making all subsequently observed writes visible to the acquiring thread.
- **synchronizes_with_release_side** (d6): The release-side endpoint of a synchronizes_with relation: an atomic operation or fence that performs a release action, making all prior memory operations visible to acquiring threads.
- **program_order** (d7): The sequential ordering of operations within a single thread as written in the source code, before any concurrent interleaving is considered.
- **inter_thread_happens_before** (d8): The subset of happens_before relations that cross thread boundaries, established by synchronizes_with connections between release and acquire operations.
- **happens_before_order** (d9): A transitive, irreflexive partial order over operations in a memory model that defines which operations must appear to precede others from any thread's perspective.

### from `deep_synchronizes_with`
- **atomic_load** (d4): load operation with memory_order semantics; load with acquire is the endpoint of synchronizes_with from release store
- **atomic_store** (d4): store operation with memory_order semantics; store with release triggers synchronizes_with on matching acquire
- **barrier_arrival** (d4): The event when a thread reaches a synchronization barrier; each arrival synchronizes-with all other arrival events at the same barrier instance, enforcing a global rendezvous.
- **condvar_broadcast** (d4): A condition variable broadcast that wakes all waiting threads; each woken thread's lock acquire synchronizes-with the broadcast operation.
- **condvar_signal** (d4): signal operation on condition variable; may synchronize_with a condvar_wait on the same condition variable and mutex
- **condvar_wait** (d4): wait operation on condition variable; releases associated mutex (release) and blocks until signal (acquire); part of condvar synchronizes_with
- **full_fence** (d4): A memory fence providing both acquire and release semantics; no memory operation on the issuing core may be reordered across the fence in either direction.
- **lock_acquire** (d4): A synchronization operation that atomically claims exclusive access to a protected region; on most architectures it is an acquire operation establishing a synchronizes-with edge with the matching release.
- **lock_release** (d4): A synchronization operation that atomically relinquishes exclusive access; it is a release operation establishing a synchronizes-with edge with all subsequent acquires of the same lock.
- **memory_order_acquire** (d4): Memory ordering barrier ensuring all loads and stores after the barrier in program order cannot be reordered before it, synchronizing with release stores.
- **memory_order_release** (d4): Memory ordering barrier ensuring all loads and stores before the barrier in program order cannot be reordered after it, making prior writes visible to acquiring threads.
- **semaphore_acquire** (d4): A decrement of a semaphore counter that claims a permit; when it succeeds the acquire synchronizes-with the release that previously published the permit.
- **semaphore_release** (d4): An increment of a semaphore counter that releases a permit; the release synchronizes-with any subsequent acquire that consumes that permit.
- **signal_delivery** (d4): The delivery of a signal to a thread creates a synchronizes-with edge from the last operation before the signal mask change to the first operation in the signal handler.
- **thread_creation** (d4): The operation of spawning a new thread of execution; the creating thread's operations before the spawn synchronizes-with the new thread's first operation in program order.
- **thread_join** (d4): joining a thread; synchronizes_with the termination of the joined thread; acquire semantics for thread's memory effects
- **memory_order_acq_rel** (d5): A memory ordering that is simultaneously acquire and release; applies to read-modify-write atomics and makes the update visible atomically with surrounding writes.
- **fence_synchronizes_with_fence** (d5): A pair of fences on different threads where the second fence in program order synchronizes-with the first fence establishing an ordering boundary.
- **fence_synchronizes_with_op** (d5): A relation where a fence on one thread establishes a synchronizes-with edge over an operation on another thread that accesses memory visible across the fence boundary.
- **unlock_synchronizes_with** (d5): A specific instance of synchronizes-with: a lock-release operation synchronizes-with the lock-acquire operation of the same lock on another thread.

---
*Projected from the `concurrency synchronization primitives and memory models` KB (377 concepts / 413 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
