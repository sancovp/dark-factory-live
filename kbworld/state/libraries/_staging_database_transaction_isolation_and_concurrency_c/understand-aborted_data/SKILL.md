# understand-aborted_data

**CALL NUMBER:** `?.aborted_data : deep_isolation_level(1)`
**DEFINITION:** The intermediate state of rows modified by a transaction that later aborted; the partial_effects_undone that existed between the first write and the rollback completion, representable as before_image/after_image pairs in the undo_log.

Invoke this skill to understand `aborted_data` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_isolation_level`
- **committed_data** (d1): database state resulting from successfully completed transactions; constitutes the visible universe for read_committed queries

## CONSUMERS (what needs this)
`aborted_state`, `aborted_state_yields_aborted_data_visibility`

---
*Projected from the `database transaction isolation and concurrency control` KB (280 concepts / 214 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*