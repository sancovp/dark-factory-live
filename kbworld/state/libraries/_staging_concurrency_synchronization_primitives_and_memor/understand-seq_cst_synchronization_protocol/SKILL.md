# understand-seq_cst_synchronization_protocol

**CALL NUMBER:** `deep_c11_memory_model.seq_cst_synchronization_protocol : concurrency_synchronization_primitives_and_memor(1)`
**DEFINITION:** The protocol by which sequentially consistent operations establish synchronization points between threads; creates a happens-before relationship across thread boundaries.

Invoke this skill to understand `seq_cst_synchronization_protocol` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `concurrency_synchronization_primitives_and_memor`
- **synchronizes_with** (d1): A relation between atomic operations in memory models where a release fence on one thread synchronizes with an acquire fence on another thread, establishing happens-before order across threads.

## CONSUMERS (what needs this)
`sequentially_consistent`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (155 concepts / 137 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*