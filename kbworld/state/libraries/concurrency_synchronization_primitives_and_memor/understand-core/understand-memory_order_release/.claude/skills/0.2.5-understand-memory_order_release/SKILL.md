---
name: 0.2.5-understand-memory_order_release
description: [0.2.5] Memory ordering barrier ensuring all loads and stores before the barrier in program order cannot be reordered 
---

# understand-memory_order_release

**CALL NUMBER:** `?.memory_order_release`
**DEFINITION:** Memory ordering barrier ensuring all loads and stores before the barrier in program order cannot be reordered after it, making prior writes visible to acquiring threads.

Invoke this skill to understand `memory_order_release` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

## CONSUMERS (what needs this)
`mcs_lock`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (211 concepts / 207 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
