# understand-uncommitted_change

**CALL NUMBER:** `deep_isolation_level.uncommitted_change`
**DEFINITION:** A modification to database state made by a transaction that has not yet committed; visible to other transactions at read_uncommitted.

Invoke this skill to understand `uncommitted_change` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

## CONSUMERS (what needs this)
`dirty_read`, `read_uncommitted`, `write_lock_not_required`

---
*Projected from the `database transaction isolation and concurrency control` KB (217 concepts / 124 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*