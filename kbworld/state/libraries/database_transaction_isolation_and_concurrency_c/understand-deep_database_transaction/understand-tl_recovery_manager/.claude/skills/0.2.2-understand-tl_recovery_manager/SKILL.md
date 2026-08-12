---
name: 0.2.2-understand-tl_recovery_manager
description: [0.2.2] The subsystem that, on system restart, reads the transaction_log from the last tl_checkpoint_record forward; r
---

# understand-tl_recovery_manager

**CALL NUMBER:** `deep_database_transaction.tl_recovery_manager`
**DEFINITION:** The subsystem that, on system restart, reads the transaction_log from the last tl_checkpoint_record forward; replays committed tl_redo_log entries and rolls back uncommitted transactions using tl_undo_log.

Invoke this skill to understand `tl_recovery_manager` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_database_transaction`
- **tl_checkpoint_record** (d1): A special log_record written periodically by a checkpoint_writer; records the volatile database state at a consistent point, bounding the recovery_manager's replay horizon.
- **tl_log_record** (d1): The fundamental unit of a transaction_log: a single append-only entry recording one atomic change or lifecycle event made by a transaction; identified by an lsn.
- **tl_redo_log** (d1): A log_record or series of tl_update_record entries capturing the after_image of modifications; replayed by recovery_manager to idempotently reconstruct committed changes after a crash.
- **tl_undo_log** (d1): A structured collection of tl_update_record entries chained by a transaction; traversed in reverse order during rollback to restore the before_image of each modified entity.
- **tl_abort_record** (d2): A log_record written when a transaction enters the aborted_state; signals that undo_log entries must be applied to reverse this transaction's effects.
- **tl_begin_record** (d2): A log_record written when a transaction transitions to the active transaction_state; records transaction_id and start timestamp but no data modifications.
- **tl_commit_record** (d2): A log_record written when a transaction commits; marks the durable persistence boundary for durability guarantees; flushed to disk before the transaction releases its locks.
- **tl_update_record** (d2): A log_record capturing a before_image and after_image of a modified data page or row; used by both redo_recovery (for durability) and undo_recovery (for atomicity rollback).
- **tl_flush_to_disk** (d3): The act of transferring the contents of tl_log_buffer to durable storage; triggered by transaction commit, tl_log_buffer overflow, or a periodic checkpoint; O(1) or O(n) bounded by buffer size.
- **tl_dirty_page_table** (d4): A runtime data structure maintained by recovery_manager listing data pages modified but not yet flushed; consulted during checkpoint to ensure write_ahead_logging invariants hold.

## CONSUMERS (what needs this)
`tl_wal_protocol`

---
*Projected from the `database transaction isolation and concurrency control` KB (217 concepts / 124 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
