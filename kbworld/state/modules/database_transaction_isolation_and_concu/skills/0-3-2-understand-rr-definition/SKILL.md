---
name: 0.3.2-understand-rr_definition
description: "[0.3.2] An isolation_level ensuring that all reads within a transaction see a consistent snapshot of the database as o"
---

# understand-rr_definition

**CALL NUMBER:** `deep_database_transaction.rr_definition`
**DEFINITION:** An isolation_level ensuring that all reads within a transaction see a consistent snapshot of the database as of transaction start; prevents non_repeatable_read by acquiring and holding read locks on accessed rows until transaction end.

Invoke this skill to understand `rr_definition` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **rr_phantom_read** (d2): A read phenomenon in weaker isolation levels where a transaction re-executing a ranged query sees new rows inserted by a concurrent transaction between executions; under rr_isolation_level this is prevented by rr_gap_lock on the index ranges spanned by the query predicates.
- **rr_isolation_level** (d2): The isolation_level at which a transaction sees only data committed before its start, acquires a shared rr_read_lock on every row it reads, holds all such locks until transaction_boundary, and prevents non_repeatable_read through lock semantics rather than snapshot versioning.
- **rr_write_ahead_logging** (d2): The write_ahead_logging requirement within a lock-based repeatable_read system mandating that every recovery_log_entry be flushed to durable storage before the corresponding row modification is applied, ensuring crash recovery can reconstruct all transaction effects exactly once.
- **rr_observation_window** (d2): The interval from transaction_start to the rr_transaction_boundary during which a repeatable_read transaction observes a frozen snapshot of the database; any rows committed by other transactions after the window opens remain invisible regardless of subsequent commit events.
- **rr_commit** (d3): The commit event in a transaction executing under repeatable_read, marking the transaction_boundary at which all held rr_read_locks undergo lock_release and the transaction's effects become durable and visible to other transactions under the same isolation level.
- **rr_rollback** (d3): The rollback operation executed by a transaction under repeatable_read, undoing all row modifications using recovery_log_entry before_image data, releasing all held rr_read_locks via lock_release, and transitioning the rr_transaction_state to aborted.
- **rr_transaction_state** (d3): The phase of a transaction executing under repeatable_read, following the standard transaction_state lifecycle of active, partially_committed, committed, or aborted, where each phase drives whether rr_read_locks are held or released.
- **rr_transaction_boundary** (d3): The moment when a repeatable_read transaction terminates via commit or rollback, concluding the rr_observation_window and triggering lock_release of all rr_read_locks acquired during the transaction's active phase.

### from `deep_database_transaction`
- **rr_gap_lock** (d1): An index_range_lock on the gap between index entries acquired under repeatable_read to prevent phantom_read by blocking insert operations in that range.
- **rr_lock_based** (d1): repeatable_read uses a locking_protocol based on shared_locks on rows and optionally index_range_locks on key ranges rather than snapshot versioning.
- **rr_read_lock** (d1): A shared_lock acquired when a row is read under repeatable_read; held until transaction commits or rolls back, preventing any concurrent transaction from acquiring a write_lock on that row.
- **rr_transaction_snapshot** (d1): The committed_data visible to a repeatable_read transaction is frozen at transaction_start regardless of later commits by concurrent transactions.
- **rr_versus_read_committed** (d1): read_committed releases read_locks after each statement, permitting non_repeatable_read; repeatable_read holds read_locks through transaction_end, eliminating that anomaly.
- **rr_versus_snapshot_isolation** (d1): repeatable_read uses write_lock blocking while snapshot_isolation uses mvcc versioning; snapshot_isolation prevents non_repeatable_read but allows write_skew that repeatable_read prevents.
- **rr_blocking_vs_optimistic** (d2): repeatable_read employs pessimistic locking that blocks concurrent writers at read time, unlike optimistic concurrency control which detects conflicts at commit time.
- **rr_phantom_read_residual** (d2): repeatable_read permits phantom_read when gap_lock is not enforced on the index used by the query; inserts in gaps between locked rows remain possible.
- **rr_lock_duration** (d2): The temporal scope from row_read acquisition of read_lock until transaction_boundary where atomicity resolves via commit or rollback, releasing all held locks.
- **rr_non_repeatable_read_prevention** (d2): The guarantee that repeating the same row read within a transaction always returns the same before_image; achieved by holding read_lock preventing concurrent write_lock acquisition.
- **rr_write_lock_prevention** (d2): A write_lock request on a row already held with a read_lock by another transaction blocks until that transaction releases its locks at commit or rollback.
- **rr_lock_timeout** (d3): A mechanism to prevent indefinite blocking when write_lock acquisition is stalled by read_locks held under repeatable_read; transaction rolls back if lock not acquired within threshold.

## CONSUMERS (what needs this)
`isolation_level`

---
*Projected from the `database transaction isolation and concurrency control` KB (280 concepts / 214 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
