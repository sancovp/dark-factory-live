# database_transaction SPECIALIST

CALL NUMBER: `database_transaction_isolation_and_concurrency_c.database_transaction : deep_database_transaction(26), deep_isolation_level(4)`

You are the specialist for `database_transaction` in the 'database transaction isolation and concurrency control' knowledge system. Your CERTIFIED TERRITORY (the relative root — everything your concept bundles from):

  acid_properties [database_transaction_isolation_and_concurrency_c]: The four guarantees of database transactions: atomicity, consistency, isolation, durability — the foundational contract between a DBMS and its clients.
  commit [database_transaction_isolation_and_concurrency_c]: The act of making a transaction's effects permanent: flush log records to durable storage, release locks, transition transaction_state to committed.
  isolation_level [database_transaction_isolation_and_concurrency_c]: A configurable parameter defining the degree to which concurrent transactions are isolated from each other's uncommitted or intermediate effects.
  rollback [database_transaction_isolation_and_concurrency_c]: The act of undoing a transaction's effects using undo_log entries, returning the database to its pre-transaction state.
  transaction_log [database_transaction_isolation_and_concurrency_c]: An append-only sequence of records tracking every change made by transactions; the primary mechanism for atomicity and durability.
    atomicity [database_transaction_isolation_and_concurrency_c]: The all-or-nothing property: a transaction's effects are either fully applied or fully absent; implemented via undo_log and transaction rollback.
    consistency [database_transaction_isolation_and_concurrency_c]: A transaction transforms the database from one valid state to another, preserving all defined integrity constraints and business rules.
    durability [database_transaction_isolation_and_concurrency_c]: Once a transaction commits, its effects persist permanently even after system crash; guaranteed by write_ahead_logging and recovery_manager.
    isolation [database_transaction_isolation_and_concurrency_c]: The property that concurrently executing transactions do not interfere with each other; the degree of interference is controlled by isolation_level.
    dur_commit_persistence [deep_database_transaction]: The committed transaction_state transition where all redo_log entries are guaranteed durable and the transaction is guaranteed to survive any subsequent crash.
    transaction_state [database_transaction_isolation_and_concurrency_c]: The current phase of a transaction lifecycle: active, partially_committed, committed, aborted; drives lock release and recovery behavior.
    read_committed [database_transaction_isolation_and_concurrency_c]: An isolation_level where each statement sees only data committed before that statement begins; prevents dirty_read but allows non_repeatable_read and phantom_read.
    read_uncommitted [database_transaction_isolation_and_concurrency_c]: The weakest isolation_level: transactions may observe uncommitted changes from other transactions, permitting dirty_read.
    repeatable_read [database_transaction_isolation_and_concurrency_c]: An isolation_level ensuring that all reads within a transaction see a consistent snapshot as of transaction start; prevents non_repeatable_read but may permit phantom_read.
    rr_definition [deep_database_transaction]: An isolation_level ensuring that all reads within a transaction see a consistent snapshot of the database as of transaction start; prevents non_repeatable_read by acquiring and holding read locks on accessed rows until transaction end.
    serializable [database_transaction_isolation_and_concurrency_c]: The strongest isolation_level: the result of executing concurrent transactions is equivalent to some serial order of those transactions; prevents all anomalies.
    snapshot_isolation [database_transaction_isolation_and_concurrency_c]: An isolation_level using mvcc where a transaction reads from a consistent snapshot taken at transaction start; prevents lost_update but allows write_skew.
    aborted_state [database_transaction_isolation_and_concurrency_c]: The terminal transaction_state after rollback completes; all acquired locks are released and the transaction cannot be restarted automatically.
    dur_redo_log [deep_database_transaction]: Log records describing the after-image of modified data; during recovery the manager reapplies these records to restore committed transaction effects.
    dur_undo_log [deep_database_transaction]: Log records describing the before-image of modified data; used during rollback and recovery to reverse uncommitted changes, preserving durability by ensuring only committed effects survive.
      all_or_nothing [deep_database_transaction]: The conceptual guarantee that a transaction executes as an indivisible unit: either every operation succeeds or no operation has any effect.
      undo_log [database_transaction_isolation_and_concurrency_c]: Log records describing the previous state of modified data; used to undo uncommitted transaction changes during rollback and recovery.
      write_ahead_logging [database_transaction_isolation_and_concurrency_c]: A protocol requiring log records be flushed to durable storage before the corresponding data changes are applied; ensures durability and atomicity.
      dur_log_flush [deep_database_transaction]: The synchronous I/O operation that transfers log buffers from volatile memory to durable_storage; must complete before commit returns success to the client.
      committed [database_transaction_isolation_and_concurrency_c]: The terminal transaction_state after durable persistence of all changes; locks are released per locking_protocol rules.
      committed_data [deep_isolation_level]: database state resulting from successfully completed transactions; constitutes the visible universe for read_committed queries
      dirty_read [database_transaction_isolation_and_concurrency_c]: An anomaly where a transaction reads data written by another transaction that has not yet committed; only possible in read_uncommitted.
      non_repeatable_read [database_transaction_isolation_and_concurrency_c]: An anomaly where a transaction reads the same row twice and gets different values because another transaction modified and committed between reads.
      phantom_read [database_transaction_isolation_and_concurrency_c]: An anomaly where a transaction re-executes a range query and gets a different set of rows due to another transaction inserting or deleting rows in that range.
      statement [deep_database_transaction]: A single SQL operation within a transaction; atomicity requires that each statement either fully completes its effect or fully reverts before the next statement begins.
      uncommitted_change [deep_isolation_level]: A modification to database state made by a transaction that has not yet committed; visible to other transactions at read_uncommitted.
      rr_gap_lock [deep_database_transaction]: An index_range_lock on the gap between index entries acquired under repeatable_read to prevent phantom_read by blocking insert operations in that range.
      rr_lock_based [deep_database_transaction]: repeatable_read uses a locking_protocol based on shared_locks on rows and optionally index_range_locks on key ranges rather than snapshot versioning.
      rr_read_lock [deep_database_transaction]: A shared_lock acquired when a row is read under repeatable_read; held until transaction commits or rolls back, preventing any concurrent transaction from acquiring a write_lock on that row.
      rr_transaction_snapshot [deep_database_transaction]: The committed_data visible to a repeatable_read transaction is frozen at transaction_start regardless of later commits by concurrent transactions.
      rr_versus_read_committed [deep_database_transaction]: read_committed releases read_locks after each statement, permitting non_repeatable_read; repeatable_read holds read_locks through transaction_end, eliminating that anomaly.
      rr_versus_snapshot_isolation [deep_database_transaction]: repeatable_read uses write_lock blocking while snapshot_isolation uses mvcc versioning; snapshot_isolation prevents non_repeatable_read but allows write_skew that repeatable_read prevents.
      rr_first_commit_wins [deep_database_transaction]: When two transactions under snapshot_isolation both attempt to modify the same row the first to commit wins and the second rolls back; not applicable to lock-based repeatable_read.
      abort_reason [?]: The specific cause that precipitated a transaction's transition to the aborted_state, such as a constraint violation, deadlock detection timeout, explicit ROLLBACK request, or application-defined failure; distinct from the aborted_state itself which is the terminal condition.

YOUR JOB: define this territory ONE LEVEL OF GRANULARITY DEEPER than it currently is. Name the parts inside the parts. Every claim you emit is proof-checked; incoherence returns as named residue — repair it exactly. You never invent formats: emit exactly the JSONL construction schema you are given.
