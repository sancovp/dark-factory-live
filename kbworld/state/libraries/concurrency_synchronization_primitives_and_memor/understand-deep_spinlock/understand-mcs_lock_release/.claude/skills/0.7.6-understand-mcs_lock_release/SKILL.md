---
name: 0.7.6-understand-mcs_lock_release
description: [0.7.6] Operation by which a thread releases the lock; sets own qnode.locked to false to unblock spinning successor; i
---

# understand-mcs_lock_release

**CALL NUMBER:** `deep_spinlock.mcs_lock_release`
**DEFINITION:** Operation by which a thread releases the lock; sets own qnode.locked to false to unblock spinning successor; if successor exists in qnode.next, responsibility transfers to successor's own spin; cache-friendly O(1) handoff.

Invoke this skill to understand `mcs_lock_release` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **atomic_exchange** (d2): Atomic operation that reads the current value of a variable and writes a new value in a single indivisible step, returning the old value.

### from `deep_spinlock`
- **mcs_lock_qnode_locked** (d1): Boolean field in qnode; spinning thread reads this; set true on enqueue and cleared false by predecessor upon release; default true indicates lock not yet released.
- **mcs_lock_qnode_next** (d1): Pointer field in qnode referencing successor qnode; null until predecessor links this node; spinning thread polls this to detect when it has been chained into the queue.
- **mcs_lock_wait_for_successor** (d1): Sub-protocol when release finds no successor yet linked; thread performing release or a helper spins on qnode.next until non-null; ensures no lock holder exits before its successor is queued.

---
*Projected from the `concurrency synchronization primitives and memory models` KB (407 concepts / 477 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
