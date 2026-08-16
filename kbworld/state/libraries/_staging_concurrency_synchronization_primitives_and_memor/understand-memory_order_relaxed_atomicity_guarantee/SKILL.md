# understand-memory_order_relaxed_atomicity_guarantee

**CALL NUMBER:** `deep_c11_memory_model.memory_order_relaxed_atomicity_guarantee : deep_synchronizes_with(20), deep_happens_before_relat(7), concurrency_synchronization_primitives_and_memor(5)`
**DEFINITION:** The indivisibility guarantee that a relaxed atomic operation completes as a single indivisible step; no intermediate state is observable by other threads during the operation, scoped to the specific atomic variable being read or written.

Invoke this skill to understand `memory_order_relaxed_atomicity_guarantee` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **atomic_cas** (d4): Compare-and-swap operation atomically loading a value, comparing it to an expected value, and storing a new value only if they matched, returning whether the swap occurred.

### from `concurrency_synchronization_primitives_and_memor`
- **happens_before_relation** (d2): A fundamental ordering relation in memory models defining that if operation A happens-before operation B, then A's effects are visible to B; forms the basis for reasoning about program correctness in concurrent settings.
- **synchronizes_with** (d2): A relation between atomic operations in memory models where a release fence on one thread synchronizes with an acquire fence on another thread, establishing happens-before order across threads.
- **acquire_semantics** (d2): Memory ordering semantics ensuring all subsequent loads/stores cannot be reordered before the acquire operation; used for lock acquisition, reading a flag after volatile write.
- **memory_order_relaxed** (d2): C11/C++11 memory ordering that only guarantees atomicity of the operation with no ordering constraints relative to other operations; allows all reorderings.
- **atomic_compare_exchange** (d3): C++11/C11 atomic operation attempting to replace expected value with desired; returns boolean indicating success; on failure, expected is updated with actual value for retry loops.

### from `deep_c11_memory_model`
- **atomic_variable_scope** (d1): The scope boundary of atomicity guarantees limited to the specific atomic variable being read or written; other variables in the program are unaffected by this atomicity property.
- **indivisibility_property** (d1): The fundamental property that a relaxed atomic operation executes as a single indivisible step from the perspective of all threads; the operation either completes fully or not at all without observable intermediate states.
- **intermediate_state_invisibility** (d1): The guarantee that no thread can observe a partially completed relaxed atomic operation; all threads observe either the state before or after the operation, never during its execution.
- **load_indivisibility** (d1): A relaxed atomic load returns exactly one value from the modification order of the target variable; no torn read of a partial value encoded in fewer bits than the atomic word is possible.
- **memory_order_relaxed_coherence_per_location** (d1): The property that each atomic variable maintains its own independent coherence order but this order is not coordinated with coherence orders of other variables; operations on separate variables are totally unordered with respect to each other.
- **memory_order_relaxed_load_value_visibility** (d1): The undefined timing of when a relaxed load obtains its value; a load may observe any value from the modification order up to that point, with no guarantee about when the load's value becomes visible to other threads.
- **memory_order_relaxed_no_ordering_constraints** (d1): The defining property that relaxed operations impose zero ordering constraints relative to any other operations on any memory location; no happens-before or synchronizes-with relationship is established with respect to other threads.
- **memory_order_relaxed_no_synchronization** (d1): The absence of any synchronization relationship; relaxed operations do not participate in the synchronizes-with relation and do not establish happens-before edges across thread boundaries regardless of visibility.
- **memory_order_relaxed_program_order_within_thread** (d1): The within-thread ordering guarantee that within a single thread, the program order of relaxed operations is still preserved for that thread's own perspective; only cross-thread visibility and cross-variable ordering are relaxed.
- **memory_order_relaxed_reordering_freedom** (d1): The freedom to reorder relaxed operations across variable boundaries; a relaxed store may be reordered with respect to a relaxed load on a different variable, and loads may observe values in an order inconsistent with program order across different locations.
- **memory_order_relaxed_store_buffering** (d1): The phenomenon that relaxed stores may be buffered in store buffers and become visible to other threads in an order different from the program order of the storing thread.
- **memory_order_relaxed_vs_acquire** (d1): The ordering contrast where acquire_semantics prevents subsequent operations from being reordered before the acquire, while memory_order_relaxed permits all such reorderings with no barrier effect.
- **memory_order_relaxed_vs_release** (d1): The ordering contrast where release_semantics prevents prior operations from being reordered after the release, while memory_order_relaxed permits all such reorderings with no barrier effect.
- **memory_order_relaxed_vs_seq_cst** (d1): The ordering contrast where sequentially_consistent imposes a single global total order visible to all threads, while memory_order_relaxed has no global ordering requirement across variables.
- **no_partial_observation** (d1): The constraint that observers of a relaxed atomic operation cannot see byte-level or word-level fragments of the operation in flight; only complete before or after states are visible.
- **no_tearing_guarantee** (d1): The guarantee that multi-byte atomic values cannot be observed in a torn state where some bytes reflect the old value and others reflect a new concurrent value.
- **per_variable_modification_order_integrity** (d1): The per-variable constraint that each atomic variable maintains a single agreed modification order even under relaxed operations; atomicity preserves this per-variable coherence order.
- **read_modify_write_indivisibility** (d1): The indivisibility of compound read-modify-write operations under relaxed ordering; fetch_add fetch_sub and similar operations complete atomically without observable intermediate states.
- **relaxed_coherence_per_location_vs_acquire_global_observation** (d1): The observation model contrast where relaxed operations on different variables maintain independent per-variable coherence orders with no cross-variable ordering coordination, while acquire semantics participates in the global sequentially consistent order when mixed with seq_cst operations.
- **relaxed_load_value_visibility_timing_vs_acquire_visibility_timing** (d1): The visibility timing contrast where a relaxed load may observe any value from the modification order at an undefined time with no guarantee about when the value becomes visible to other threads, while an acquire load observes the value at a specific point in the happens-before order with guaranteed visibility semantics.
- **relaxed_mod_order_indivisibility** (d1): Each modification order entry appears as an indivisible step; no intermediate store state is visible during the store, bounded by memory_order_relaxed_atomicity_guarantee.
- **relaxed_mod_order_store_append** (d1): A relaxed store operation to atomic M atomically appends to the end of M's modification order; this append is indivisible and creates a new last element visible to all threads according to the order.
- **relaxed_no_happens_before_edge_vs_acquire_hb_edge** (d1): The ordering contrast where relaxed operations never establish a happens-before edge with operations on other threads regardless of visibility timing, while acquire semantics combined with release on another thread creates a transitive happens-before edge connecting the release writer to the acquire reader.
- **relaxed_no_ordering_constraints_vs_acquire_subsequent_constrained** (d1): The scope contrast where relaxed operations impose zero ordering constraints on any other operations on any memory location, while acquire semantics constrains all subsequent loads and stores in the same thread to remain after the acquire in program order.
- **relaxed_no_synchronizes_with_vs_acquire_synchronizes_with** (d1): The synchronization contrast where relaxed atomic operations do not participate in the synchronizes-with relation and establish no cross-thread ordering, while acquire operations on a matching release create a synchronizes-with relationship establishing inter-thread happens-before.

### from `deep_happens_before_relat`
- **acquire_fence** (d4): A memory ordering primitive that ensures all load and store operations appearing after the fence in program order do not begin until the fence completes and all prior writes are visible.
- **release_fence** (d4): A memory ordering primitive that ensures all load and store operations appearing before the fence in program order complete before any operations appearing after the fence begin.
- **synchronizes_with_acquire_side** (d5): The acquire-side endpoint of a synchronizes_with relation: an atomic operation or fence that performs an acquire action, making all subsequently observed writes visible to the acquiring thread.
- **synchronizes_with_release_side** (d5): The release-side endpoint of a synchronizes_with relation: an atomic operation or fence that performs a release action, making all prior memory operations visible to acquiring threads.
- **program_order** (d6): The sequential ordering of operations within a single thread as written in the source code, before any concurrent interleaving is considered.
- **inter_thread_happens_before** (d7): The subset of happens_before relations that cross thread boundaries, established by synchronizes_with connections between release and acquire operations.
- **happens_before_order** (d8): A transitive, irreflexive partial order over operations in a memory model that defines which operations must appear to precede others from any thread's perspective.

### from `deep_synchronizes_with`
- **atomic_load** (d3): load operation with memory_order semantics; load with acquire is the endpoint of synchronizes_with from release store
- **atomic_store** (d3): store operation with memory_order semantics; store with release triggers synchronizes_with on matching acquire
- **barrier_arrival** (d3): The event when a thread reaches a synchronization barrier; each arrival synchronizes-with all other arrival events at the same barrier instance, enforcing a global rendezvous.
- **condvar_broadcast** (d3): A condition variable broadcast that wakes all waiting threads; each woken thread's lock acquire synchronizes-with the broadcast operation.
- **condvar_signal** (d3): signal operation on condition variable; may synchronize_with a condvar_wait on the same condition variable and mutex
- **condvar_wait** (d3): wait operation on condition variable; releases associated mutex (release) and blocks until signal (acquire); part of condvar synchronizes_with
- **full_fence** (d3): A memory fence providing both acquire and release semantics; no memory operation on the issuing core may be reordered across the fence in either direction.
- **lock_acquire** (d3): A synchronization operation that atomically claims exclusive access to a protected region; on most architectures it is an acquire operation establishing a synchronizes-with edge with the matching release.
- **lock_release** (d3): A synchronization operation that atomically relinquishes exclusive access; it is a release operation establishing a synchronizes-with edge with all subsequent acquires of the same lock.
- **memory_order_acquire** (d3): Memory ordering barrier ensuring all loads and stores after the barrier in program order cannot be reordered before it, synchronizing with release stores.
- **memory_order_release** (d3): Memory ordering barrier ensuring all loads and stores before the barrier in program order cannot be reordered after it, making prior writes visible to acquiring threads.
- **semaphore_acquire** (d3): A decrement of a semaphore counter that claims a permit; when it succeeds the acquire synchronizes-with the release that previously published the permit.
- **semaphore_release** (d3): An increment of a semaphore counter that releases a permit; the release synchronizes-with any subsequent acquire that consumes that permit.
- **signal_delivery** (d3): The delivery of a signal to a thread creates a synchronizes-with edge from the last operation before the signal mask change to the first operation in the signal handler.
- **thread_creation** (d3): The operation of spawning a new thread of execution; the creating thread's operations before the spawn synchronizes-with the new thread's first operation in program order.
- **thread_join** (d3): joining a thread; synchronizes_with the termination of the joined thread; acquire semantics for thread's memory effects
- **memory_order_acq_rel** (d4): A memory ordering that is simultaneously acquire and release; applies to read-modify-write atomics and makes the update visible atomically with surrounding writes.
- **fence_synchronizes_with_fence** (d4): A pair of fences on different threads where the second fence in program order synchronizes-with the first fence establishing an ordering boundary.
- **fence_synchronizes_with_op** (d4): A relation where a fence on one thread establishes a synchronizes-with edge over an operation on another thread that accesses memory visible across the fence boundary.
- **unlock_synchronizes_with** (d4): A specific instance of synchronizes-with: a lock-release operation synchronizes-with the lock-acquire operation of the same lock on another thread.

## CONSUMERS (what needs this)
`memory_order_relaxed`, `memory_order_relaxed_atomicity_guarantee_implies_load_store_atomicity`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (377 concepts / 413 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*