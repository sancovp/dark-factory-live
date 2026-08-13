---
name: 0.1.4-understand-mcs_lock
description: "[0.1.4] Queued lock where each waiting thread spins on a locally-owned node linked into a queue; cache-friendly with o"
---

# understand-mcs_lock

**CALL NUMBER:** `concurrency_synchronization_primitives_and_memor.mcs_lock`
**DEFINITION:** Queued lock where each waiting thread spins on a locally-owned node linked into a queue; cache-friendly with only O(1) bus traffic per lock acquisition; named after Mellor-Crummey and Scott.

Invoke this skill to understand `mcs_lock` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **atomic_cas** (d1): Compare-and-swap operation atomically loading a value, comparing it to an expected value, and storing a new value only if they matched, returning whether the swap occurred.
- **atomic_exchange** (d1): Atomic operation that reads the current value of a variable and writes a new value in a single indivisible step, returning the old value.
- **memory_order_acquire** (d1): Memory ordering barrier ensuring all loads and stores after the barrier in program order cannot be reordered before it, synchronizing with release stores.
- **memory_order_release** (d1): Memory ordering barrier ensuring all loads and stores before the barrier in program order cannot be reordered after it, making prior writes visible to acquiring threads.

## CONSUMERS (what needs this)
`clh_lock`, `spinlock`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (155 concepts / 137 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
