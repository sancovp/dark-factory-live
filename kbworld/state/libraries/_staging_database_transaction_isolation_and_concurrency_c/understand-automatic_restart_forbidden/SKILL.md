# understand-automatic_restart_forbidden

**CALL NUMBER:** `?.automatic_restart_forbidden`
**DEFINITION:** A protocol constraint requiring that a transaction in the aborted_state cannot be re-executed automatically by the database; the application must explicitly reissue the transaction, distinguishing abort from retryable failure.

Invoke this skill to understand `automatic_restart_forbidden` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

## CONSUMERS (what needs this)
`aborted_state`, `aborted_state_forbids_automatic_restart`

---
*Projected from the `database transaction isolation and concurrency control` KB (280 concepts / 214 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*