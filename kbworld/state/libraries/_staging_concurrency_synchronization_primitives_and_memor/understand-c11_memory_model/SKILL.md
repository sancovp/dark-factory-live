# understand-c11_memory_model

**CALL NUMBER:** `concurrency_synchronization_primitives_and_memor.c11_memory_model : deep_c11_memory_model(52), deep_synchronizes_with(20), deep_indivisibility_prope(9), deep_happens_before_relat(7)`
**DEFINITION:** Standard C11 specification defining memory orderings: memory_order_relaxed, memory_order_consume, memory_order_acquire, memory_order_release, memory_order_acq_rel, memory_order_seq_cst; defines happens-before and synchronizes-with relations.

Invoke this skill to understand `c11_memory_model` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **atomic_cas** (d4): Compare-and-swap operation atomically loading a value, comparing it to an expected value, and storing a new value only if they matched, returning whether the swap occurred.

### from `concurrency_synchronization_primitives_and_memor`
- **acquire_semantics** (d1): Memory ordering semantics ensuring all subsequent loads/stores cannot be reordered before the acquire operation; used for lock acquisition, reading a flag after volatile write.
- **happens_before_relation** (d1): A fundamental ordering relation in memory models defining that if operation A happens-before operation B, then A's effects are visible to B; forms the basis for reasoning about program correctness in concurrent settings.
- **memory_order_relaxed** (d1): C11/C++11 memory ordering that only guarantees atomicity of the operation with no ordering constraints relative to other operations; allows all reorderings.
- **release_semantics** (d1): Memory ordering semantics ensuring all prior loads/stores cannot be reordered after the release operation; used for lock release, writing data before a volatile flag.
- **sequentially_consistent** (d1): The strongest memory ordering requiring a single total order of all sequentially consistent operations visible to all threads; implied by default for std::atomic operations in C++.
- **synchronizes_with** (d2): A relation between atomic operations in memory models where a release fence on one thread synchronizes with an acquire fence on another thread, establishing happens-before order across threads.
- **atomic_compare_exchange** (d3): C++11/C11 atomic operation attempting to replace expected value with desired; returns boolean indicating success; on failure, expected is updated with actual value for retry loops.

### from `deep_c11_memory_model`
- **memory_order_relaxed_vs_acquire** (d2): The ordering contrast where acquire_semantics prevents subsequent operations from being reordered before the acquire, while memory_order_relaxed permits all such reorderings with no barrier effect.
- **relaxed_mod_order_visibility_timing_undefined** (d2): A store's position in the modification order does not determine when other threads observe it; relaxed loads may observe stale values with no bound on staleness, contrasting with acquire-visibility guarantees.
- **indivisibility_property** (d2): The fundamental property that a relaxed atomic operation executes as a single indivisible step from the perspective of all threads; the operation either completes fully or not at all without observable intermediate states.
- **memory_order_relaxed_atomicity_guarantee** (d2): The indivisibility guarantee that a relaxed atomic operation completes as a single indivisible step; no intermediate state is observable by other threads during the operation, scoped to the specific atomic variable being read or written.
- **memory_order_relaxed_coherence_per_location** (d2): The property that each atomic variable maintains its own independent coherence order but this order is not coordinated with coherence orders of other variables; operations on separate variables are totally unordered with respect to each other.
- **memory_order_relaxed_load_value_visibility** (d2): The undefined timing of when a relaxed load obtains its value; a load may observe any value from the modification order up to that point, with no guarantee about when the load's value becomes visible to other threads.
- **memory_order_relaxed_modification_order** (d2): The per-variable constraint that each atomic variable still has a well-defined modification order agreed upon by all threads, even though relaxed operations on different variables are unconstrained relative to each other.
- **memory_order_relaxed_no_ordering_constraints** (d2): The defining property that relaxed operations impose zero ordering constraints relative to any other operations on any memory location; no happens-before or synchronizes-with relationship is established with respect to other threads.
- **memory_order_relaxed_no_synchronization** (d2): The absence of any synchronization relationship; relaxed operations do not participate in the synchronizes-with relation and do not establish happens-before edges across thread boundaries regardless of visibility.
- **memory_order_relaxed_program_order_within_thread** (d2): The within-thread ordering guarantee that within a single thread, the program order of relaxed operations is still preserved for that thread's own perspective; only cross-thread visibility and cross-variable ordering are relaxed.
- **memory_order_relaxed_reordering_freedom** (d2): The freedom to reorder relaxed operations across variable boundaries; a relaxed store may be reordered with respect to a relaxed load on a different variable, and loads may observe values in an order inconsistent with program order across different locations.
- **memory_order_relaxed_store_buffering** (d2): The phenomenon that relaxed stores may be buffered in store buffers and become visible to other threads in an order different from the program order of the storing thread.
- **no_tearing_guarantee** (d2): The guarantee that multi-byte atomic values cannot be observed in a torn state where some bytes reflect the old value and others reflect a new concurrent value.
- **relaxed_mod_order_def** (d2): The well-defined sequential order of all store operations to a single atomic variable; every relaxed store to variable x appends to x's modification order in some position, and all threads agree on this order for x.
- **memory_order_relaxed_vs_release** (d2): The ordering contrast where release_semantics prevents prior operations from being reordered after the release, while memory_order_relaxed permits all such reorderings with no barrier effect.
- **memory_order_relaxed_vs_seq_cst** (d2): The ordering contrast where sequentially_consistent imposes a single global total order visible to all threads, while memory_order_relaxed has no global ordering requirement across variables.
- **relaxed_mod_order_thread_agreement** (d2): Although relaxed operations impose no ordering constraints, all threads nevertheless agree on the modification order for any given atomic variable; this agreement is a property of the machine model, not of synchronization.
- **seq_cst_atomic_visibility** (d2): The guarantee that all threads observe the effects of a sequentially consistent operation at the same logical point in the global total order; reads observe the most recent write in the total order.
- **seq_cst_default_atomic_ordering** (d2): The default memory ordering for std::atomic operations in C11/C++11 when no memory_order is explicitly specified; provides the strongest guarantees without requiring explicit fence code.
- **seq_cst_fence** (d2): The explicit memory fence with sequentially consistent ordering that provides both acquire and release semantics plus additional ordering constraints to enforce the global total order.
- **seq_cst_global_total_order** (d2): A single total order of all sequentially consistent operations that is visible and agreed upon by all threads in the system; the interleaving point where all threads observe the same sequence of operations.
- **seq_cst_implies_acquire** (d2): A load operation with sequentially consistent ordering carries acquire semantics; all subsequent loads and stores cannot be reordered before the seq_cst load.
- **seq_cst_implies_release** (d2): A store operation with sequentially consistent ordering carries release semantics; all prior loads and stores cannot be reordered after the seq_cst store.
- **seq_cst_indivisible_atomicity** (d2): The property that each sequentially consistent operation appears indivisible and instantaneous to all observers; no intermediate states are visible during the operation.
- **seq_cst_program_order_preservation** (d2): Within each thread, sequentially consistent operations maintain program order; no reordering of these operations is permitted within the same thread.

### from `deep_happens_before_relat`
- **acquire_fence** (d4): A memory ordering primitive that ensures all load and store operations appearing after the fence in program order do not begin until the fence completes and all prior writes are visible.
- **release_fence** (d4): A memory ordering primitive that ensures all load and store operations appearing before the fence in program order complete before any operations appearing after the fence begin.
- **synchronizes_with_acquire_side** (d5): The acquire-side endpoint of a synchronizes_with relation: an atomic operation or fence that performs an acquire action, making all subsequently observed writes visible to the acquiring thread.
- **synchronizes_with_release_side** (d5): The release-side endpoint of a synchronizes_with relation: an atomic operation or fence that performs a release action, making all prior memory operations visible to acquiring threads.
- **program_order** (d6): The sequential ordering of operations within a single thread as written in the source code, before any concurrent interleaving is considered.
- **inter_thread_happens_before** (d7): The subset of happens_before relations that cross thread boundaries, established by synchronizes_with connections between release and acquire operations.
- **happens_before_order** (d8): A transitive, irreflexive partial order over operations in a memory model that defines which operations must appear to precede others from any thread's perspective.

### from `deep_indivisibility_prope`
- **isi_atomicity_boundary** (d4): The demarcation line separating the before-state from the after-state of a relaxed atomic operation; no observable execution window exists across this boundary.
- **isi_operation_completeness** (d5): The property that a relaxed atomic operation executes to full completion before any observer can witness its effect or lack thereof; partial execution is undetectable.
- **isi_no_in_flight_state** (d6): The guaranteed absence of any transient value during operation execution that could be sampled by a concurrent thread; the in-flight state is logically invisible.
- **isi_post_state_visibility** (d6): The state of the target atomic variable after the operation has fully completed, which is the only alternative state an observer may witness.
- **isi_pre_state_visibility** (d6): The state of the target atomic variable as it existed before the operation commenced, which is the only alternative state an observer may witness.
- **isi_load_visibility_rule** (d7): For a relaxed atomic load, the read returns exactly one value from the modification order; no torn read of a partial encoding is observable.
- **isi_rmw_visibility_rule** (d7): For a relaxed read-modify-write operation, observers see either the complete state before the modification or the complete state after modification; the read-modify-write executes atomically without observable intermediate stages.
- **isi_store_visibility_rule** (d7): For a relaxed atomic store, any reading thread observes either the complete value that existed before the store or the complete value after the store; torn writes are impossible.
- **isi_observer_exclusivity** (d7): The constraint that any given observer of a relaxed atomic operation sees exclusively one of the two complete states; mixed or hybrid observations are prohibited.

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
- **fence_synchronizes_with_fence** (d3): A pair of fences on different threads where the second fence in program order synchronizes-with the first fence establishing an ordering boundary.
- **memory_order_acq_rel** (d4): A memory ordering that is simultaneously acquire and release; applies to read-modify-write atomics and makes the update visible atomically with surrounding writes.
- **fence_synchronizes_with_op** (d4): A relation where a fence on one thread establishes a synchronizes-with edge over an operation on another thread that accesses memory visible across the fence boundary.
- **unlock_synchronizes_with** (d4): A specific instance of synchronizes-with: a lock-release operation synchronizes-with the lock-acquire operation of the same lock on another thread.

## CONSUMERS (what needs this)
`c11_atomic_thread_fence_contrast`, `cpp11_memory_model`, `data_race`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (407 concepts / 477 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*