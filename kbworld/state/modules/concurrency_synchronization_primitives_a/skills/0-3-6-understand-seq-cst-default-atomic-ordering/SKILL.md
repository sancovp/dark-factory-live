---
name: 0.3.6-understand-seq_cst_default_atomic_ordering
description: "[0.3.6] The default memory ordering for std::atomic operations in C11/C++11 when no memory_order is explicitly specifi"
---

# understand-seq_cst_default_atomic_ordering

**CALL NUMBER:** `deep_c11_memory_model.seq_cst_default_atomic_ordering : deep_synchronizes_with(20), deep_happens_before_relat(7), concurrency_synchronization_primitives_and_memor(3)`
**DEFINITION:** The default memory ordering for std::atomic operations in C11/C++11 when no memory_order is explicitly specified; provides the strongest guarantees without requiring explicit fence code.

Invoke this skill to understand `seq_cst_default_atomic_ordering` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **atomic_cas** (d5): Compare-and-swap operation atomically loading a value, comparing it to an expected value, and storing a new value only if they matched, returning whether the swap occurred.

### from `concurrency_synchronization_primitives_and_memor`
- **happens_before_relation** (d2): A fundamental ordering relation in memory models defining that if operation A happens-before operation B, then A's effects are visible to B; forms the basis for reasoning about program correctness in concurrent settings.
- **synchronizes_with** (d3): A relation between atomic operations in memory models where a release fence on one thread synchronizes with an acquire fence on another thread, establishing happens-before order across threads.
- **atomic_compare_exchange** (d4): C++11/C11 atomic operation attempting to replace expected value with desired; returns boolean indicating success; on failure, expected is updated with actual value for retry loops.

### from `deep_c11_memory_model`
- **seq_cst_default_semantics** (d1): The implicit behavior that std::atomic operations exhibit when instantiated without an explicit memory_order template argument; this is the mandated strongest ordering level requiring no explicit fences.
- **seq_cst_global_total_order** (d1): A single total order of all sequentially consistent operations that is visible and agreed upon by all threads in the system; the interleaving point where all threads observe the same sequence of operations.
- **seq_cst_indivisible_atomicity** (d1): The property that each sequentially consistent operation appears indivisible and instantaneous to all observers; no intermediate states are visible during the operation.
- **seq_cst_program_order_preservation** (d1): Within each thread, sequentially consistent operations maintain program order; no reordering of these operations is permitted within the same thread.
- **seq_cst_synchronizes_with** (d1): A relation between release_seq_cst operations on one thread and acquire_seq_cst operations on another thread that establishes inter-thread happens-before ordering through the global total order.
- **seq_cst_no_explicit_fence_required** (d2): The property that the sequentially consistent default provides the full barrier effect of a seq_cst fence without requiring the programmer to write one; the compiler inserts the necessary barriers automatically.
- **seq_cst_atomic_visibility** (d2): The guarantee that all threads observe the effects of a sequentially consistent operation at the same logical point in the global total order; reads observe the most recent write in the total order.
- **seq_cst_fence** (d2): The explicit memory fence with sequentially consistent ordering that provides both acquire and release semantics plus additional ordering constraints to enforce the global total order.
- **seq_cst_implies_acquire** (d2): A load operation with sequentially consistent ordering carries acquire semantics; all subsequent loads and stores cannot be reordered before the seq_cst load.
- **seq_cst_implies_release** (d2): A store operation with sequentially consistent ordering carries release semantics; all prior loads and stores cannot be reordered after the seq_cst store.
- **seq_cst_happens_before_edge** (d2): A transitive ordering relation established between sequentially consistent operations that creates visibility guarantees across thread boundaries; if A happens-before B, A's effects are visible to B.
- **seq_cst_default_implies_seq_cst_fence** (d3): The equivalence between an operation using the default seq_cst ordering and the same operation paired with an explicit seq_cst fence; both establish the same global ordering constraints.

### from `deep_happens_before_relat`
- **acquire_fence** (d5): A memory ordering primitive that ensures all load and store operations appearing after the fence in program order do not begin until the fence completes and all prior writes are visible.
- **release_fence** (d5): A memory ordering primitive that ensures all load and store operations appearing before the fence in program order complete before any operations appearing after the fence begin.
- **synchronizes_with_acquire_side** (d6): The acquire-side endpoint of a synchronizes_with relation: an atomic operation or fence that performs an acquire action, making all subsequently observed writes visible to the acquiring thread.
- **synchronizes_with_release_side** (d6): The release-side endpoint of a synchronizes_with relation: an atomic operation or fence that performs a release action, making all prior memory operations visible to acquiring threads.
- **program_order** (d7): The sequential ordering of operations within a single thread as written in the source code, before any concurrent interleaving is considered.
- **inter_thread_happens_before** (d8): The subset of happens_before relations that cross thread boundaries, established by synchronizes_with connections between release and acquire operations.
- **happens_before_order** (d9): A transitive, irreflexive partial order over operations in a memory model that defines which operations must appear to precede others from any thread's perspective.

### from `deep_synchronizes_with`
- **fence_synchronizes_with_fence** (d3): A pair of fences on different threads where the second fence in program order synchronizes-with the first fence establishing an ordering boundary.
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
- **fence_synchronizes_with_op** (d5): A relation where a fence on one thread establishes a synchronizes-with edge over an operation on another thread that accesses memory visible across the fence boundary.
- **unlock_synchronizes_with** (d5): A specific instance of synchronizes-with: a lock-release operation synchronizes-with the lock-acquire operation of the same lock on another thread.

## CONSUMERS (what needs this)
`sequentially_consistent`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (407 concepts / 477 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
