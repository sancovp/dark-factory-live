# understand-aborted_state

**CALL NUMBER:** `database_transaction_isolation_and_concurrency_c.aborted_state : deep_isolation_level(1)`
**DEFINITION:** The terminal transaction_state after rollback completes; all acquired locks are released and the transaction cannot be restarted automatically.

Invoke this skill to understand `aborted_state` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **abort_reason** (d1): The specific cause that precipitated a transaction's transition to the aborted_state, such as a constraint violation, deadlock detection timeout, explicit ROLLBACK request, or application-defined failure; distinct from the aborted_state itself which is the terminal condition.
- **aborted_data** (d1): The intermediate state of rows modified by a transaction that later aborted; the partial_effects_undone that existed between the first write and the rollback completion, representable as before_image/after_image pairs in the undo_log.
- **automatic_restart_forbidden** (d1): A protocol constraint requiring that a transaction in the aborted_state cannot be re-executed automatically by the database; the application must explicitly reissue the transaction, distinguishing abort from retryable failure.
- **lock_release** (d1): The deterministic act of relinquishing every lock held by a transaction upon reaching its transaction_boundary, whether through commit or abort, restoring exclusive or shared access rights to the affected rows and index entries for other transactions.
- **partial_effects_undone** (d1): The invariant that upon rollback all modifications performed by the transaction are reversed to match the before_image recorded in each recovery_log_entry, leaving no residual trace of the transaction's intermediate state in the database.
- **recovery_log_entry** (d1): A durable record written to the transaction log capturing a single row modification, containing the transaction identifier, the affected row identifier, the before_image, and the after_image; the recovery_subsystem uses these entries to undo uncommitted changes and redo committed changes during crash recovery.
- **recovery_subsystem** (d2): The database component responsible for restoring consistency after a crash by scanning the transaction log, classifying each transaction as committed uncommitted or aborted, and executing undo operations for uncommitted transactions using their recovery_log_entry records.

### from `database_transaction_isolation_and_concurrency_c`
- **transaction_id** (d1): A monotonically increasing identifier assigned to each transaction; the basis for snapshot_isolation read_view construction and visibility_check.
- **transaction_state** (d2): The current phase of a transaction lifecycle: active, partially_committed, committed, aborted; drives lock release and recovery behavior.
- **committed** (d3): The terminal transaction_state after durable persistence of all changes; locks are released per locking_protocol rules.

### from `deep_isolation_level`
- **committed_data** (d2): database state resulting from successfully completed transactions; constitutes the visible universe for read_committed queries

## CONSUMERS (what needs this)
`rollback`, `transaction_state`

---
*Projected from the `database transaction isolation and concurrency control` KB (280 concepts / 214 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*