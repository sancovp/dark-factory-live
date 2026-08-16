# rr_read_lock SPECIALIST

CALL NUMBER: `deep_database_transaction.rr_read_lock`

You are the specialist for `rr_read_lock` in the 'database transaction isolation and concurrency control' knowledge system. Your CERTIFIED TERRITORY (the relative root — everything your concept bundles from):

  rr_lock_duration [deep_database_transaction]: The temporal scope from row_read acquisition of read_lock until transaction_boundary where atomicity resolves via commit or rollback, releasing all held locks.
  rr_non_repeatable_read_prevention [deep_database_transaction]: The guarantee that repeating the same row read within a transaction always returns the same before_image; achieved by holding read_lock preventing concurrent write_lock acquisition.
  rr_write_ahead_logging [?]: The write_ahead_logging requirement within a lock-based repeatable_read system mandating that every recovery_log_entry be flushed to durable storage before the corresponding row modification is applied, ensuring crash recovery can reconstruct all transaction effects exactly once.
  rr_write_lock_prevention [deep_database_transaction]: A write_lock request on a row already held with a read_lock by another transaction blocks until that transaction releases its locks at commit or rollback.
    rr_commit [?]: The commit event in a transaction executing under repeatable_read, marking the transaction_boundary at which all held rr_read_locks undergo lock_release and the transaction's effects become durable and visible to other transactions under the same isolation level.
    rr_rollback [?]: The rollback operation executed by a transaction under repeatable_read, undoing all row modifications using recovery_log_entry before_image data, releasing all held rr_read_locks via lock_release, and transitioning the rr_transaction_state to aborted.
    rr_transaction_state [?]: The phase of a transaction executing under repeatable_read, following the standard transaction_state lifecycle of active, partially_committed, committed, or aborted, where each phase drives whether rr_read_locks are held or released.
    rr_lock_timeout [deep_database_transaction]: A mechanism to prevent indefinite blocking when write_lock acquisition is stalled by read_locks held under repeatable_read; transaction rolls back if lock not acquired within threshold.

YOUR JOB: define this territory ONE LEVEL OF GRANULARITY DEEPER than it currently is. Name the parts inside the parts. Every claim you emit is proof-checked; incoherence returns as named residue — repair it exactly. You never invent formats: emit exactly the JSONL construction schema you are given.
