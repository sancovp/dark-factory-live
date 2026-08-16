# understand-recovery_log_entry

**CALL NUMBER:** `?.recovery_log_entry`
**DEFINITION:** A durable record written to the transaction log capturing a single row modification, containing the transaction identifier, the affected row identifier, the before_image, and the after_image; the recovery_subsystem uses these entries to undo uncommitted changes and redo committed changes during crash recovery.

Invoke this skill to understand `recovery_log_entry` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **recovery_subsystem** (d1): The database component responsible for restoring consistency after a crash by scanning the transaction log, classifying each transaction as committed uncommitted or aborted, and executing undo operations for uncommitted transactions using their recovery_log_entry records.

## CONSUMERS (what needs this)
`aborted_state`, `aborted_state_creates_recovery_log_entry`

---
*Projected from the `database transaction isolation and concurrency control` KB (280 concepts / 214 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*