# understand-tl_undo_log

**CALL NUMBER:** `deep_database_transaction.tl_undo_log`
**DEFINITION:** A structured collection of tl_update_record entries chained by a transaction; traversed in reverse order during rollback to restore the before_image of each modified entity.

Invoke this skill to understand `tl_undo_log` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_database_transaction`
- **tl_abort_record** (d1): A log_record written when a transaction enters the aborted_state; signals that undo_log entries must be applied to reverse this transaction's effects.

## CONSUMERS (what needs this)
`tl_recovery_manager`, `tl_update_record`

---
*Projected from the `database transaction isolation and concurrency control` KB (217 concepts / 124 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*