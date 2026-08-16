# understand-atomic_cas

**CALL NUMBER:** `?.atomic_cas`
**DEFINITION:** Compare-and-swap operation atomically loading a value, comparing it to an expected value, and storing a new value only if they matched, returning whether the swap occurred.

Invoke this skill to understand `atomic_cas` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

## CONSUMERS (what needs this)
`atomic_compare_exchange`, `mcs_lock`, `mcs_lock_enqueue`, `mcs_lock_tail`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (277 concepts / 278 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*