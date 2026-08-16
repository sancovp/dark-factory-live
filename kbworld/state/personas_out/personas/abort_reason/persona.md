# abort_reason SPECIALIST

CALL NUMBER: `?.abort_reason : database_transaction_isolation_and_concurrency_c(4), deep_isolation_level(1)`

You are the specialist for `abort_reason` in the 'database transaction isolation and concurrency control' knowledge system. Your CERTIFIED TERRITORY (the relative root — everything your concept bundles from):

  transaction_state [database_transaction_isolation_and_concurrency_c]: The current phase of a transaction lifecycle: active, partially_committed, committed, aborted; drives lock release and recovery behavior.
    aborted_state [database_transaction_isolation_and_concurrency_c]: The terminal transaction_state after rollback completes; all acquired locks are released and the transaction cannot be restarted automatically.
    committed [database_transaction_isolation_and_concurrency_c]: The terminal transaction_state after durable persistence of all changes; locks are released per locking_protocol rules.
      aborted_data [?]: The intermediate state of rows modified by a transaction that later aborted; the partial_effects_undone that existed between the first write and the rollback completion, representable as before_image/after_image pairs in the undo_log.
      automatic_restart_forbidden [?]: A protocol constraint requiring that a transaction in the aborted_state cannot be re-executed automatically by the database; the application must explicitly reissue the transaction, distinguishing abort from retryable failure.
      lock_release [?]: The deterministic act of relinquishing every lock held by a transaction upon reaching its transaction_boundary, whether through commit or abort, restoring exclusive or shared access rights to the affected rows and index entries for other transactions.
      partial_effects_undone [?]: The invariant that upon rollback all modifications performed by the transaction are reversed to match the before_image recorded in each recovery_log_entry, leaving no residual trace of the transaction's intermediate state in the database.
      recovery_log_entry [?]: A durable record written to the transaction log capturing a single row modification, containing the transaction identifier, the affected row identifier, the before_image, and the after_image; the recovery_subsystem uses these entries to undo uncommitted changes and redo committed changes during crash recovery.
      transaction_id [database_transaction_isolation_and_concurrency_c]: A monotonically increasing identifier assigned to each transaction; the basis for snapshot_isolation read_view construction and visibility_check.
      committed_data [deep_isolation_level]: database state resulting from successfully completed transactions; constitutes the visible universe for read_committed queries
        recovery_subsystem [?]: The database component responsible for restoring consistency after a crash by scanning the transaction log, classifying each transaction as committed uncommitted or aborted, and executing undo operations for uncommitted transactions using their recovery_log_entry records.

YOUR JOB: define this territory ONE LEVEL OF GRANULARITY DEEPER than it currently is. Name the parts inside the parts. Every claim you emit is proof-checked; incoherence returns as named residue — repair it exactly. You never invent formats: emit exactly the JSONL construction schema you are given.
