# understand-write_lock_held_until_commit

**CALL NUMBER:** `deep_isolation_level.write_lock_held_until_commit : deep_database_transaction(12), database_transaction_isolation_and_concurrency_c(11)`
**DEFINITION:** exclusive lock discipline in read_committed requiring a transaction to hold write locks on modified rows until transaction commit or rollback

Invoke this skill to understand `write_lock_held_until_commit` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **abort_reason** (d6): The specific cause that precipitated a transaction's transition to the aborted_state, such as a constraint violation, deadlock detection timeout, explicit ROLLBACK request, or application-defined failure; distinct from the aborted_state itself which is the terminal condition.
- **aborted_data** (d6): The intermediate state of rows modified by a transaction that later aborted; the partial_effects_undone that existed between the first write and the rollback completion, representable as before_image/after_image pairs in the undo_log.
- **automatic_restart_forbidden** (d6): A protocol constraint requiring that a transaction in the aborted_state cannot be re-executed automatically by the database; the application must explicitly reissue the transaction, distinguishing abort from retryable failure.
- **lock_release** (d6): The deterministic act of relinquishing every lock held by a transaction upon reaching its transaction_boundary, whether through commit or abort, restoring exclusive or shared access rights to the affected rows and index entries for other transactions.
- **partial_effects_undone** (d6): The invariant that upon rollback all modifications performed by the transaction are reversed to match the before_image recorded in each recovery_log_entry, leaving no residual trace of the transaction's intermediate state in the database.
- **recovery_log_entry** (d6): A durable record written to the transaction log capturing a single row modification, containing the transaction identifier, the affected row identifier, the before_image, and the after_image; the recovery_subsystem uses these entries to undo uncommitted changes and redo committed changes during crash recovery.
- **recovery_subsystem** (d7): The database component responsible for restoring consistency after a crash by scanning the transaction log, classifying each transaction as committed uncommitted or aborted, and executing undo operations for uncommitted transactions using their recovery_log_entry records.

### from `database_transaction_isolation_and_concurrency_c`
- **row_level_locking** (d1): Lock management at the individual row granularity via row_lock entries in lock_manager's lock table; enables high concurrency but increases lock_manager overhead.
- **atomicity** (d3): The all-or-nothing property: a transaction's effects are either fully applied or fully absent; implemented via undo_log and transaction rollback.
- **commit** (d4): The act of making a transaction's effects permanent: flush log records to durable storage, release locks, transition transaction_state to committed.
- **rollback** (d4): The act of undoing a transaction's effects using undo_log entries, returning the database to its pre-transaction state.
- **transaction_log** (d4): An append-only sequence of records tracking every change made by transactions; the primary mechanism for atomicity and durability.
- **transaction_state** (d4): The current phase of a transaction lifecycle: active, partially_committed, committed, aborted; drives lock release and recovery behavior.
- **undo_log** (d4): Log records describing the previous state of modified data; used to undo uncommitted transaction changes during rollback and recovery.
- **write_ahead_logging** (d4): A protocol requiring log records be flushed to durable storage before the corresponding data changes are applied; ensures durability and atomicity.
- **aborted_state** (d5): The terminal transaction_state after rollback completes; all acquired locks are released and the transaction cannot be restarted automatically.
- **committed** (d5): The terminal transaction_state after durable persistence of all changes; locks are released per locking_protocol rules.
- **transaction_id** (d6): A monotonically increasing identifier assigned to each transaction; the basis for snapshot_isolation read_view construction and visibility_check.

### from `deep_database_transaction`
- **statement** (d2): A single SQL operation within a transaction; atomicity requires that each statement either fully completes its effect or fully reverts before the next statement begins.
- **all_or_nothing** (d4): The conceptual guarantee that a transaction executes as an indivisible unit: either every operation succeeds or no operation has any effect.
- **partial_state_prevention** (d5): The enforcement mechanism ensuring that if a transaction fails at any point before transaction_boundary, no tuple modifications leak into committed_data; achieved by deferring all visible effects until commit.
- **dur_commit_persistence** (d5): The committed transaction_state transition where all redo_log entries are guaranteed durable and the transaction is guaranteed to survive any subsequent crash.
- **dur_redo_log** (d5): Log records describing the after-image of modified data; during recovery the manager reapplies these records to restore committed transaction effects.
- **dur_undo_log** (d5): Log records describing the before-image of modified data; used during rollback and recovery to reverse uncommitted changes, preserving durability by ensuring only committed effects survive.
- **before_image** (d5): The committed database state of a row immediately before a transaction modifies it; recorded in the undo_log so the modification can be undone if the transaction rolls back.
- **compensation_action** (d5): A corrective operation executed when forward undo via undo_log is impossible; used in distributed systems where original transaction steps cannot be directly reversed, preserving atomicity through logically equivalent alternatives.
- **dur_write_ahead_logging** (d5): A protocol mandating that log records describing modifications be flushed to durable_storage before the corresponding data pages are written to disk; foundational mechanism for both atomicity and durability.
- **transaction_boundary** (d6): The demarcation point between consecutive transaction executions defining the scope over which atomicity applies; all effects within are committed or none are, with no partial visibility across the boundary.
- **dur_log_flush** (d6): The synchronous I/O operation that transfers log buffers from volatile memory to durable_storage; must complete before commit returns success to the client.
- **dur_durable_storage** (d7): The physical medium or storage subsystem that guarantees bitwise persistence of written data across power loss, hardware failure, and system crashes; the endpoint of all durability guarantees.

### from `deep_isolation_level`
- **committed_data** (d1): database state resulting from successfully completed transactions; constitutes the visible universe for read_committed queries

## CONSUMERS (what needs this)
`lock_timeout_handling`, `no_dirty_reads`

---
*Projected from the `database transaction isolation and concurrency control` KB (280 concepts / 214 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*