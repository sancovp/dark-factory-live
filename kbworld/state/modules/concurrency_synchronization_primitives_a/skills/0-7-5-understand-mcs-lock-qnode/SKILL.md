---
name: 0.7.5-understand-mcs_lock_qnode
description: "[0.7.5] Thread-local queue node containing locked flag and successor pointer; must be cache-aligned and allocated per-"
---

# understand-mcs_lock_qnode

**CALL NUMBER:** `deep_spinlock.mcs_lock_qnode`
**DEFINITION:** Thread-local queue node containing locked flag and successor pointer; must be cache-aligned and allocated per-thread to enable local spinning without shared contention.

Invoke this skill to understand `mcs_lock_qnode` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **cache_alignment** (d1): Placement of data structures on memory boundaries matching cache line size, typically 64 bytes, preventing false sharing between adjacent data.

## CONSUMERS (what needs this)
`mcs_lock_acquire`, `mcs_lock_local_spinning`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (407 concepts / 477 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
