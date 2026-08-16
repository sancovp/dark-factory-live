# understand-seq_cst_atomic_visibility

**CALL NUMBER:** `deep_c11_memory_model.seq_cst_atomic_visibility`
**DEFINITION:** The guarantee that all threads observe the effects of a sequentially consistent operation at the same logical point in the global total order; reads observe the most recent write in the total order.

Invoke this skill to understand `seq_cst_atomic_visibility` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

## CONSUMERS (what needs this)
`hb_seq_cst_boundary`, `sequentially_consistent`, `sw_seq_cst_atomic_op`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (277 concepts / 278 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*