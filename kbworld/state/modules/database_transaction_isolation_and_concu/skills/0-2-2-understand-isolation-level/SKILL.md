---
name: 0.2.2-understand-isolation_level
description: "[0.2.2] A configurable parameter defining the degree to which concurrent transactions are isolated from each other's u"
---

# understand-isolation_level

**CALL NUMBER:** `database_transaction_isolation_and_concurrency_c.isolation_level : deep_database_transaction(26), deep_isolation_level(4)`
**DEFINITION:** A configurable parameter defining the degree to which concurrent transactions are isolated from each other's uncommitted or intermediate effects.

Invoke this skill to understand `isolation_level` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **rr_phantom_read** (d3): A read phenomenon in weaker isolation levels where a transaction re-executing a ranged query sees new rows inserted by a concurrent transaction between executions; under rr_isolation_level this is prevented by rr_gap_lock on the index ranges spanned by the query predicates.
- **rr_isolation_level** (d3): The isolation_level at which a transaction sees only data committed before its start, acquires a shared rr_read_lock on every row it reads, holds all such locks until transaction_boundary, and prevents non_repeatable_read through lock semantics rather than snapshot versioning.
- **rr_write_ahead_logging** (d3): The write_ahead_logging requirement within a lock-based repeatable_read system mandating that every recovery_log_entry be flushed to durable storage before the corresponding row modification is applied, ensuring crash recovery can reconstruct all transaction effects exactly once.
- **rr_observation_window** (d3): The interval from transaction_start to the rr_transaction_boundary during which a repeatable_read transaction observes a frozen snapshot of the database; any rows committed by other transactions after the window opens remain invisible regardless of subsequent commit events.
- **rr_transaction_state** (d3): The phase of a transaction executing under repeatable_read, following the standard transaction_state lifecycle of active, partially_committed, committed, or aborted, where each phase drives whether rr_read_locks are held or released.
- **rr_commit** (d4): The commit event in a transaction executing under repeatable_read, marking the transaction_boundary at which all held rr_read_locks undergo lock_release and the transaction's effects become durable and visible to other transactions under the same isolation level.
- **rr_rollback** (d4): The rollback operation executed by a transaction under repeatable_read, undoing all row modifications using recovery_log_entry before_image data, releasing all held rr_read_locks via lock_release, and transitioning the rr_transaction_state to aborted.
- **rr_transaction_boundary** (d4): The moment when a repeatable_read transaction terminates via commit or rollback, concluding the rr_observation_window and triggering lock_release of all rr_read_locks acquired during the transaction's active phase.
- **abort_reason** (d6): The specific cause that precipitated a transaction's transition to the aborted_state, such as a constraint violation, deadlock detection timeout, explicit ROLLBACK request, or application-defined failure; distinct from the aborted_state itself which is the terminal condition.
- **aborted_data** (d6): The intermediate state of rows modified by a transaction that later aborted; the partial_effects_undone that existed between the first write and the rollback completion, representable as before_image/after_image pairs in the undo_log.
- **automatic_restart_forbidden** (d6): A protocol constraint requiring that a transaction in the aborted_state cannot be re-executed automatically by the database; the application must explicitly reissue the transaction, distinguishing abort from retryable failure.
- **lock_release** (d6): The deterministic act of relinquishing every lock held by a transaction upon reaching its transaction_boundary, whether through commit or abort, restoring exclusive or shared access rights to the affected rows and index entries for other transactions.
- **partial_effects_undone** (d6): The invariant that upon rollback all modifications performed by the transaction are reversed to match the before_image recorded in each recovery_log_entry, leaving no residual trace of the transaction's intermediate state in the database.
- **recovery_log_entry** (d6): A durable record written to the transaction log capturing a single row modification, containing the transaction identifier, the affected row identifier, the before_image, and the after_image; the recovery_subsystem uses these entries to undo uncommitted changes and redo committed changes during crash recovery.
- **recovery_subsystem** (d7): The database component responsible for restoring consistency after a crash by scanning the transaction log, classifying each transaction as committed uncommitted or aborted, and executing undo operations for uncommitted transactions using their recovery_log_entry records.

### from `database_transaction_isolation_and_concurrency_c`
- **read_committed** (d1): An isolation_level where each statement sees only data committed before that statement begins; prevents dirty_read but allows non_repeatable_read and phantom_read.
- **read_uncommitted** (d1): The weakest isolation_level: transactions may observe uncommitted changes from other transactions, permitting dirty_read.
- **repeatable_read** (d1): An isolation_level ensuring that all reads within a transaction see a consistent snapshot as of transaction start; prevents non_repeatable_read but may permit phantom_read.
- **serializable** (d1): The strongest isolation_level: the result of executing concurrent transactions is equivalent to some serial order of those transactions; prevents all anomalies.
- **snapshot_isolation** (d1): An isolation_level using mvcc where a transaction reads from a consistent snapshot taken at transaction start; prevents lost_update but allows write_skew.
- **dirty_read** (d2): An anomaly where a transaction reads data written by another transaction that has not yet committed; only possible in read_uncommitted.
- **non_repeatable_read** (d2): An anomaly where a transaction reads the same row twice and gets different values because another transaction modified and committed between reads.
- **phantom_read** (d2): An anomaly where a transaction re-executes a range query and gets a different set of rows due to another transaction inserting or deleting rows in that range.
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
- **rr_definition** (d1): An isolation_level ensuring that all reads within a transaction see a consistent snapshot of the database as of transaction start; prevents non_repeatable_read by acquiring and holding read locks on accessed rows until transaction end.
- **statement** (d2): A single SQL operation within a transaction; atomicity requires that each statement either fully completes its effect or fully reverts before the next statement begins.
- **rr_gap_lock** (d2): An index_range_lock on the gap between index entries acquired under repeatable_read to prevent phantom_read by blocking insert operations in that range.
- **rr_lock_based** (d2): repeatable_read uses a locking_protocol based on shared_locks on rows and optionally index_range_locks on key ranges rather than snapshot versioning.
- **rr_read_lock** (d2): A shared_lock acquired when a row is read under repeatable_read; held until transaction commits or rolls back, preventing any concurrent transaction from acquiring a write_lock on that row.
- **rr_transaction_snapshot** (d2): The committed_data visible to a repeatable_read transaction is frozen at transaction_start regardless of later commits by concurrent transactions.
- **rr_versus_read_committed** (d2): read_committed releases read_locks after each statement, permitting non_repeatable_read; repeatable_read holds read_locks through transaction_end, eliminating that anomaly.
- **rr_versus_snapshot_isolation** (d2): repeatable_read uses write_lock blocking while snapshot_isolation uses mvcc versioning; snapshot_isolation prevents non_repeatable_read but allows write_skew that repeatable_read prevents.
- **rr_first_commit_wins** (d2): When two transactions under snapshot_isolation both attempt to modify the same row the first to commit wins and the second rolls back; not applicable to lock-based repeatable_read.
- **rr_blocking_vs_optimistic** (d3): repeatable_read employs pessimistic locking that blocks concurrent writers at read time, unlike optimistic concurrency control which detects conflicts at commit time.
- **rr_phantom_read_residual** (d3): repeatable_read permits phantom_read when gap_lock is not enforced on the index used by the query; inserts in gaps between locked rows remain possible.
- **rr_lock_duration** (d3): The temporal scope from row_read acquisition of read_lock until transaction_boundary where atomicity resolves via commit or rollback, releasing all held locks.
- **rr_non_repeatable_read_prevention** (d3): The guarantee that repeating the same row read within a transaction always returns the same before_image; achieved by holding read_lock preventing concurrent write_lock acquisition.
- **rr_write_lock_prevention** (d3): A write_lock request on a row already held with a read_lock by another transaction blocks until that transaction releases its locks at commit or rollback.
- **all_or_nothing** (d4): The conceptual guarantee that a transaction executes as an indivisible unit: either every operation succeeds or no operation has any effect.
- **rr_lock_timeout** (d4): A mechanism to prevent indefinite blocking when write_lock acquisition is stalled by read_locks held under repeatable_read; transaction rolls back if lock not acquired within threshold.
- **partial_state_prevention** (d5): The enforcement mechanism ensuring that if a transaction fails at any point before transaction_boundary, no tuple modifications leak into committed_data; achieved by deferring all visible effects until commit.
- **dur_commit_persistence** (d5): The committed transaction_state transition where all redo_log entries are guaranteed durable and the transaction is guaranteed to survive any subsequent crash.
- **dur_redo_log** (d5): Log records describing the after-image of modified data; during recovery the manager reapplies these records to restore committed transaction effects.
- **dur_undo_log** (d5): Log records describing the before-image of modified data; used during rollback and recovery to reverse uncommitted changes, preserving durability by ensuring only committed effects survive.
- **before_image** (d5): The committed database state of a row immediately before a transaction modifies it; recorded in the undo_log so the modification can be undone if the transaction rolls back.
- **compensation_action** (d5): A corrective operation executed when forward undo via undo_log is impossible; used in distributed systems where original transaction steps cannot be directly reversed, preserving atomicity through logically equivalent alternatives.
- **dur_write_ahead_logging** (d5): A protocol mandating that log records describing modifications be flushed to durable_storage before the corresponding data pages are written to disk; foundational mechanism for both atomicity and durability.
- **transaction_boundary** (d6): The demarcation point between consecutive transaction executions defining the scope over which atomicity applies; all effects within are committed or none are, with no partial visibility across the boundary.
- **dur_log_flush** (d6): The synchronous I/O operation that transfers log buffers from volatile memory to durable_storage; must complete before commit returns success to the client.

### from `deep_isolation_level`
- **committed_data** (d2): database state resulting from successfully completed transactions; constitutes the visible universe for read_committed queries
- **uncommitted_change** (d2): A modification to database state made by a transaction that has not yet committed; visible to other transactions at read_uncommitted.
- **transaction_read** (d3): The act of a transaction executing a read operation; at read_uncommitted this read may return uncommitted_change from concurrent transactions.
- **observation_window** (d4): The temporal scope during which a reading transaction may see uncommitted changes from other transactions, bounded by those transactions' commit operations.

## CONSUMERS (what needs this)
`concurrency_level`, `database_transaction`, `isolation`, `read_committed`

---
*Projected from the `database transaction isolation and concurrency control` KB (280 concepts / 214 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
