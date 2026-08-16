# understand-partial_effects_undone

**CALL NUMBER:** `?.partial_effects_undone`
**DEFINITION:** The invariant that upon rollback all modifications performed by the transaction are reversed to match the before_image recorded in each recovery_log_entry, leaving no residual trace of the transaction's intermediate state in the database.

Invoke this skill to understand `partial_effects_undone` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

## CONSUMERS (what needs this)
`aborted_state`, `aborted_state_contains_partial_effects_undone`

---
*Projected from the `database transaction isolation and concurrency control` KB (280 concepts / 214 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*