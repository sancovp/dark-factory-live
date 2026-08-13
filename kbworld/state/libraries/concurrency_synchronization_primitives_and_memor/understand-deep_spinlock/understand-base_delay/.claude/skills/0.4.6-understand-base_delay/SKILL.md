---
name: 0.4.6-understand-base_delay
description: [0.4.6] Initial wait time in nanoseconds or microseconds before the first lock acquisition retry; the starting point o
---

# understand-base_delay

**CALL NUMBER:** `deep_spinlock.base_delay`
**DEFINITION:** Initial wait time in nanoseconds or microseconds before the first lock acquisition retry; the starting point of the exponential schedule.

Invoke this skill to understand `base_delay` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

## CONSUMERS (what needs this)
`current_delay`, `exponential_backoff`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (155 concepts / 137 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
