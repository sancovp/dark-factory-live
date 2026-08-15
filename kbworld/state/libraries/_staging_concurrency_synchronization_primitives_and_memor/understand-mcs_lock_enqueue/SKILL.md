# understand-mcs_lock_enqueue

**CALL NUMBER:** `deep_spinlock.mcs_lock_enqueue`
**DEFINITION:** Operation appending a thread-local qnode to the queue tail; atomically CASes qnode into tail; on CAS failure, completes the predecessor's link and retries; ensures FIFO acquisition order.

Invoke this skill to understand `mcs_lock_enqueue` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **atomic_cas** (d1): Compare-and-swap operation atomically loading a value, comparing it to an expected value, and storing a new value only if they matched, returning whether the swap occurred.

### from `deep_spinlock`
- **mcs_lock_help_links** (d1): Backoff resolution protocol during failed enqueue CAS; the thread that lost the CAS follows the discovered pointer chain to complete the linking work of the winner before retrying its own append; prevents starvation under high contention.

## CONSUMERS (what needs this)
`mcs_lock_acquire`, `mcs_lock_fifo_ordering`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (211 concepts / 207 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*