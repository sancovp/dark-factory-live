---
name: 0.1.3-understand-sequentially_consistent
description: [0.1.3] The strongest memory ordering requiring a single total order of all sequentially consistent operations visible
---

# understand-sequentially_consistent

**CALL NUMBER:** `concurrency_synchronization_primitives_and_memor.sequentially_consistent : deep_synchronizes_with(20), deep_c11_memory_model(16), deep_happens_before_relat(7)`
**DEFINITION:** The strongest memory ordering requiring a single total order of all sequentially consistent operations visible to all threads; implied by default for std::atomic operations in C++.

Invoke this skill to understand `sequentially_consistent` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **atomic_cas** (d4): Compare-and-swap operation atomically loading a value, comparing it to an expected value, and storing a new value only if they matched, returning whether the swap occurred.

### from `concurrency_synchronization_primitives_and_memor`
- **happens_before_relation** (d2): A fundamental ordering relation in memory models defining that if operation A happens-before operation B, then A's effects are visible to B; forms the basis for reasoning about program correctness in concurrent settings.
- **synchronizes_with** (d2): A relation between atomic operations in memory models where a release fence on one thread synchronizes with an acquire fence on another thread, establishing happens-before order across threads.
- **atomic_compare_exchange** (d3): C++11/C11 atomic operation attempting to replace expected value with desired; returns boolean indicating success; on failure, expected is updated with actual value for retry loops.

### from `deep_c11_memory_model`
- **memory_order_relaxed_vs_seq_cst** (d1): The ordering contrast where sequentially_consistent imposes a single global total order visible to all threads, while memory_order_relaxed has no global ordering requirement across variables.
- **relaxed_mod_order_thread_agreement** (d1): Although relaxed operations impose no ordering constraints, all threads nevertheless agree on the modification order for any given atomic variable; this agreement is a property of the machine model, not of synchronization.
- **seq_cst_atomic_visibility** (d1): The guarantee that all threads observe the effects of a sequentially consistent operation at the same logical point in the global total order; reads observe the most recent write in the total order.
- **seq_cst_default_atomic_ordering** (d1): The default memory ordering for std::atomic operations in C11/C++11 when no memory_order is explicitly specified; provides the strongest guarantees without requiring explicit fence code.
- **seq_cst_fence** (d1): The explicit memory fence with sequentially consistent ordering that provides both acquire and release semantics plus additional ordering constraints to enforce the global total order.
- **seq_cst_global_total_order** (d1): A single total order of all sequentially consistent operations that is visible and agreed upon by all threads in the system; the interleaving point where all threads observe the same sequence of operations.
- **seq_cst_implies_acquire** (d1): A load operation with sequentially consistent ordering carries acquire semantics; all subsequent loads and stores cannot be reordered before the seq_cst load.
- **seq_cst_implies_release** (d1): A store operation with sequentially consistent ordering carries release semantics; all prior loads and stores cannot be reordered after the seq_cst store.
- **seq_cst_indivisible_atomicity** (d1): The property that each sequentially consistent operation appears indivisible and instantaneous to all observers; no intermediate states are visible during the operation.
- **seq_cst_program_order_preservation** (d1): Within each thread, sequentially consistent operations maintain program order; no reordering of these operations is permitted within the same thread.
- **seq_cst_synchronization_protocol** (d1): The protocol by which sequentially consistent operations establish synchronization points between threads; creates a happens-before relationship across thread boundaries.
- **seq_cst_default_semantics** (d2): The implicit behavior that std::atomic operations exhibit when instantiated without an explicit memory_order template argument; this is the mandated strongest ordering level requiring no explicit fences.
- **seq_cst_synchronizes_with** (d2): A relation between release_seq_cst operations on one thread and acquire_seq_cst operations on another thread that establishes inter-thread happens-before ordering through the global total order.
- **seq_cst_happens_before_edge** (d2): A transitive ordering relation established between sequentially consistent operations that creates visibility guarantees across thread boundaries; if A happens-before B, A's effects are visible to B.
- **seq_cst_no_explicit_fence_required** (d3): The property that the sequentially consistent default provides the full barrier effect of a seq_cst fence without requiring the programmer to write one; the compiler inserts the necessary barriers automatically.
- **seq_cst_default_implies_seq_cst_fence** (d4): The equivalence between an operation using the default seq_cst ordering and the same operation paired with an explicit seq_cst fence; both establish the same global ordering constraints.

### from `deep_happens_before_relat`
- **acquire_fence** (d4): A memory ordering primitive that ensures all load and store operations appearing after the fence in program order do not begin until the fence completes and all prior writes are visible.
- **release_fence** (d4): A memory ordering primitive that ensures all load and store operations appearing before the fence in program order complete before any operations appearing after the fence begin.
- **synchronizes_with_acquire_side** (d5): The acquire-side endpoint of a synchronizes_with relation: an atomic operation or fence that performs an acquire action, making all subsequently observed writes visible to the acquiring thread.
- **synchronizes_with_release_side** (d5): The release-side endpoint of a synchronizes_with relation: an atomic operation or fence that performs a release action, making all prior memory operations visible to acquiring threads.
- **program_order** (d6): The sequential ordering of operations within a single thread as written in the source code, before any concurrent interleaving is considered.
- **inter_thread_happens_before** (d7): The subset of happens_before relations that cross thread boundaries, established by synchronizes_with connections between release and acquire operations.
- **happens_before_order** (d8): A transitive, irreflexive partial order over operations in a memory model that defines which operations must appear to precede others from any thread's perspective.

### from `deep_synchronizes_with`
- **fence_synchronizes_with_fence** (d2): A pair of fences on different threads where the second fence in program order synchronizes-with the first fence establishing an ordering boundary.
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
- **fence_synchronizes_with_op** (d4): A relation where a fence on one thread establishes a synchronizes-with edge over an operation on another thread that accesses memory visible across the fence boundary.
- **unlock_synchronizes_with** (d4): A specific instance of synchronizes-with: a lock-release operation synchronizes-with the lock-acquire operation of the same lock on another thread.

## CONSUMERS (what needs this)
`c11_memory_model`, `load_buffering_allowed`, `modification_order_coherence`, `relaxed_vs_seq_cst`, `seq_cst_atomic_visibility_all_threads_agree_on_visibility_sequence`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (407 concepts / 477 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
