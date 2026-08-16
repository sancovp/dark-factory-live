---
name: 0.1.5-understand-happens_before_relation
description: "[0.1.5] A fundamental ordering relation in memory models defining that if operation A happens-before operation B, then"
---

# understand-happens_before_relation

**CALL NUMBER:** `concurrency_synchronization_primitives_and_memor.happens_before_relation : deep_synchronizes_with(20), deep_happens_before_relat(7), deep_c11_memory_model(1)`
**DEFINITION:** A fundamental ordering relation in memory models defining that if operation A happens-before operation B, then A's effects are visible to B; forms the basis for reasoning about program correctness in concurrent settings.

Invoke this skill to understand `happens_before_relation` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **atomic_cas** (d3): Compare-and-swap operation atomically loading a value, comparing it to an expected value, and storing a new value only if they matched, returning whether the swap occurred.

### from `concurrency_synchronization_primitives_and_memor`
- **synchronizes_with** (d1): A relation between atomic operations in memory models where a release fence on one thread synchronizes with an acquire fence on another thread, establishing happens-before order across threads.
- **atomic_compare_exchange** (d2): C++11/C11 atomic operation attempting to replace expected value with desired; returns boolean indicating success; on failure, expected is updated with actual value for retry loops.

### from `deep_c11_memory_model`
- **seq_cst_fence** (d2): The explicit memory fence with sequentially consistent ordering that provides both acquire and release semantics plus additional ordering constraints to enforce the global total order.

### from `deep_happens_before_relat`
- **acquire_fence** (d3): A memory ordering primitive that ensures all load and store operations appearing after the fence in program order do not begin until the fence completes and all prior writes are visible.
- **release_fence** (d3): A memory ordering primitive that ensures all load and store operations appearing before the fence in program order complete before any operations appearing after the fence begin.
- **synchronizes_with_acquire_side** (d4): The acquire-side endpoint of a synchronizes_with relation: an atomic operation or fence that performs an acquire action, making all subsequently observed writes visible to the acquiring thread.
- **synchronizes_with_release_side** (d4): The release-side endpoint of a synchronizes_with relation: an atomic operation or fence that performs a release action, making all prior memory operations visible to acquiring threads.
- **program_order** (d5): The sequential ordering of operations within a single thread as written in the source code, before any concurrent interleaving is considered.
- **inter_thread_happens_before** (d6): The subset of happens_before relations that cross thread boundaries, established by synchronizes_with connections between release and acquire operations.
- **happens_before_order** (d7): A transitive, irreflexive partial order over operations in a memory model that defines which operations must appear to precede others from any thread's perspective.

### from `deep_synchronizes_with`
- **atomic_load** (d2): load operation with memory_order semantics; load with acquire is the endpoint of synchronizes_with from release store
- **atomic_store** (d2): store operation with memory_order semantics; store with release triggers synchronizes_with on matching acquire
- **barrier_arrival** (d2): The event when a thread reaches a synchronization barrier; each arrival synchronizes-with all other arrival events at the same barrier instance, enforcing a global rendezvous.
- **condvar_broadcast** (d2): A condition variable broadcast that wakes all waiting threads; each woken thread's lock acquire synchronizes-with the broadcast operation.
- **condvar_signal** (d2): signal operation on condition variable; may synchronize_with a condvar_wait on the same condition variable and mutex
- **condvar_wait** (d2): wait operation on condition variable; releases associated mutex (release) and blocks until signal (acquire); part of condvar synchronizes_with
- **full_fence** (d2): A memory fence providing both acquire and release semantics; no memory operation on the issuing core may be reordered across the fence in either direction.
- **lock_acquire** (d2): A synchronization operation that atomically claims exclusive access to a protected region; on most architectures it is an acquire operation establishing a synchronizes-with edge with the matching release.
- **lock_release** (d2): A synchronization operation that atomically relinquishes exclusive access; it is a release operation establishing a synchronizes-with edge with all subsequent acquires of the same lock.
- **memory_order_acquire** (d2): Memory ordering barrier ensuring all loads and stores after the barrier in program order cannot be reordered before it, synchronizing with release stores.
- **memory_order_release** (d2): Memory ordering barrier ensuring all loads and stores before the barrier in program order cannot be reordered after it, making prior writes visible to acquiring threads.
- **semaphore_acquire** (d2): A decrement of a semaphore counter that claims a permit; when it succeeds the acquire synchronizes-with the release that previously published the permit.
- **semaphore_release** (d2): An increment of a semaphore counter that releases a permit; the release synchronizes-with any subsequent acquire that consumes that permit.
- **signal_delivery** (d2): The delivery of a signal to a thread creates a synchronizes-with edge from the last operation before the signal mask change to the first operation in the signal handler.
- **thread_creation** (d2): The operation of spawning a new thread of execution; the creating thread's operations before the spawn synchronizes-with the new thread's first operation in program order.
- **thread_join** (d2): joining a thread; synchronizes_with the termination of the joined thread; acquire semantics for thread's memory effects
- **memory_order_acq_rel** (d3): A memory ordering that is simultaneously acquire and release; applies to read-modify-write atomics and makes the update visible atomically with surrounding writes.
- **fence_synchronizes_with_fence** (d3): A pair of fences on different threads where the second fence in program order synchronizes-with the first fence establishing an ordering boundary.
- **fence_synchronizes_with_op** (d3): A relation where a fence on one thread establishes a synchronizes-with edge over an operation on another thread that accesses memory visible across the fence boundary.
- **unlock_synchronizes_with** (d3): A specific instance of synchronizes-with: a lock-release operation synchronizes-with the lock-acquire operation of the same lock on another thread.

## CONSUMERS (what needs this)
`c11_memory_model`, `memory_order_relaxed`, `no_happens_before_establishment`, `relaxed_no_happens_before_edge_vs_acquire_hb_edge`, `seq_cst_atomic_visibility_happens_before_cutoff_visibility`, `seq_cst_atomic_visibility_observation_consistency_rule`, `seq_cst_global_total_order`, `synchronizes_with_absence`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (377 concepts / 413 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
