# rr_definition SPECIALIST

CALL NUMBER: `deep_database_transaction.rr_definition`

You are the specialist for `rr_definition` in the 'database transaction isolation and concurrency control' knowledge system. Your CERTIFIED TERRITORY (the relative root — everything your concept bundles from):

  rr_gap_lock [deep_database_transaction]: An index_range_lock on the gap between index entries acquired under repeatable_read to prevent phantom_read by blocking insert operations in that range.
  rr_lock_based [deep_database_transaction]: repeatable_read uses a locking_protocol based on shared_locks on rows and optionally index_range_locks on key ranges rather than snapshot versioning.
  rr_read_lock [deep_database_transaction]: A shared_lock acquired when a row is read under repeatable_read; held until transaction commits or rolls back, preventing any concurrent transaction from acquiring a write_lock on that row.
  rr_transaction_snapshot [deep_database_transaction]: The committed_data visible to a repeatable_read transaction is frozen at transaction_start regardless of later commits by concurrent transactions.
  rr_versus_read_committed [deep_database_transaction]: read_committed releases read_locks after each statement, permitting non_repeatable_read; repeatable_read holds read_locks through transaction_end, eliminating that anomaly.
  rr_versus_snapshot_isolation [deep_database_transaction]: repeatable_read uses write_lock blocking while snapshot_isolation uses mvcc versioning; snapshot_isolation prevents non_repeatable_read but allows write_skew that repeatable_read prevents.
    rr_phantom_read [?]: A read phenomenon in weaker isolation levels where a transaction re-executing a ranged query sees new rows inserted by a concurrent transaction between executions; under rr_isolation_level this is prevented by rr_gap_lock on the index ranges spanned by the query predicates.
    rr_blocking_vs_optimistic [deep_database_transaction]: repeatable_read employs pessimistic locking that blocks concurrent writers at read time, unlike optimistic concurrency control which detects conflicts at commit time.
    rr_isolation_level [?]: The isolation_level at which a transaction sees only data committed before its start, acquires a shared rr_read_lock on every row it reads, holds all such locks until transaction_boundary, and prevents non_repeatable_read through lock semantics rather than snapshot versioning.
    rr_phantom_read_residual [deep_database_transaction]: repeatable_read permits phantom_read when gap_lock is not enforced on the index used by the query; inserts in gaps between locked rows remain possible.
    rr_lock_duration [deep_database_transaction]: The temporal scope from row_read acquisition of read_lock until transaction_boundary where atomicity resolves via commit or rollback, releasing all held locks.
    rr_non_repeatable_read_prevention [deep_database_transaction]: The guarantee that repeating the same row read within a transaction always returns the same before_image; achieved by holding read_lock preventing concurrent write_lock acquisition.
    rr_write_ahead_logging [?]: The write_ahead_logging requirement within a lock-based repeatable_read system mandating that every recovery_log_entry be flushed to durable storage before the corresponding row modification is applied, ensuring crash recovery can reconstruct all transaction effects exactly once.
    rr_write_lock_prevention [deep_database_transaction]: A write_lock request on a row already held with a read_lock by another transaction blocks until that transaction releases its locks at commit or rollback.
    rr_observation_window [?]: The interval from transaction_start to the rr_transaction_boundary during which a repeatable_read transaction observes a frozen snapshot of the database; any rows committed by other transactions after the window opens remain invisible regardless of subsequent commit events.
      rr_commit [?]: The commit event in a transaction executing under repeatable_read, marking the transaction_boundary at which all held rr_read_locks undergo lock_release and the transaction's effects become durable and visible to other transactions under the same isolation level.
      rr_rollback [?]: The rollback operation executed by a transaction under repeatable_read, undoing all row modifications using recovery_log_entry before_image data, releasing all held rr_read_locks via lock_release, and transitioning the rr_transaction_state to aborted.
      rr_transaction_state [?]: The phase of a transaction executing under repeatable_read, following the standard transaction_state lifecycle of active, partially_committed, committed, or aborted, where each phase drives whether rr_read_locks are held or released.
      rr_lock_timeout [deep_database_transaction]: A mechanism to prevent indefinite blocking when write_lock acquisition is stalled by read_locks held under repeatable_read; transaction rolls back if lock not acquired within threshold.
      rr_transaction_boundary [?]: The moment when a repeatable_read transaction terminates via commit or rollback, concluding the rr_observation_window and triggering lock_release of all rr_read_locks acquired during the transaction's active phase.

YOUR JOB: define this territory ONE LEVEL OF GRANULARITY DEEPER than it currently is. Name the parts inside the parts. Every claim you emit is proof-checked; incoherence returns as named residue — repair it exactly. You never invent formats: emit exactly the JSONL construction schema you are given.
