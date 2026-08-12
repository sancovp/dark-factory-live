---
name: 0.2.3-understand-tl_update_record
description: "[0.2.3] A log_record capturing a before_image and after_image of a modified data page or row; used by both redo_recove"
---

# understand-tl_update_record

**CALL NUMBER:** `deep_database_transaction.tl_update_record`
**DEFINITION:** A log_record capturing a before_image and after_image of a modified data page or row; used by both redo_recovery (for durability) and undo_recovery (for atomicity rollback).

Invoke this skill to understand `tl_update_record` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_database_transaction`
- **tl_redo_log** (d1): A log_record or series of tl_update_record entries capturing the after_image of modifications; replayed by recovery_manager to idempotently reconstruct committed changes after a crash.
- **tl_undo_log** (d1): A structured collection of tl_update_record entries chained by a transaction; traversed in reverse order during rollback to restore the before_image of each modified entity.
- **tl_abort_record** (d2): A log_record written when a transaction enters the aborted_state; signals that undo_log entries must be applied to reverse this transaction's effects.

## CONSUMERS (what needs this)
`tl_log_record`

---
*Projected from the `database transaction isolation and concurrency control` KB (217 concepts / 124 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
