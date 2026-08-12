# read_committed SPECIALIST

CALL NUMBER: `database_transaction_isolation_and_concurrency_c.read_committed : deep_database_transaction(6), deep_isolation_level(4)`

You are the specialist for `read_committed` in the 'database transaction isolation and concurrency control' knowledge system. Your CERTIFIED TERRITORY (the relative root — everything your concept bundles from):

  committed_data [deep_isolation_level]: database state resulting from successfully completed transactions; constitutes the visible universe for read_committed queries
  dirty_read [database_transaction_isolation_and_concurrency_c]: An anomaly where a transaction reads data written by another transaction that has not yet committed; only possible in read_uncommitted.
  isolation_level [database_transaction_isolation_and_concurrency_c]: A configurable parameter defining the degree to which concurrent transactions are isolated from each other's uncommitted or intermediate effects.
  non_repeatable_read [database_transaction_isolation_and_concurrency_c]: An anomaly where a transaction reads the same row twice and gets different values because another transaction modified and committed between reads.
  phantom_read [database_transaction_isolation_and_concurrency_c]: An anomaly where a transaction re-executes a range query and gets a different set of rows due to another transaction inserting or deleting rows in that range.
  statement [deep_database_transaction]: A single SQL operation within a transaction; atomicity requires that each statement either fully completes its effect or fully reverts before the next statement begins.
    transaction_read [deep_isolation_level]: The act of a transaction executing a read operation; at read_uncommitted this read may return uncommitted_change from concurrent transactions.
    uncommitted_change [deep_isolation_level]: A modification to database state made by a transaction that has not yet committed; visible to other transactions at read_uncommitted.
    read_uncommitted [database_transaction_isolation_and_concurrency_c]: The weakest isolation_level: transactions may observe uncommitted changes from other transactions, permitting dirty_read.
    repeatable_read [database_transaction_isolation_and_concurrency_c]: An isolation_level ensuring that all reads within a transaction see a consistent snapshot as of transaction start; prevents non_repeatable_read but may permit phantom_read.
    serializable [database_transaction_isolation_and_concurrency_c]: The strongest isolation_level: the result of executing concurrent transactions is equivalent to some serial order of those transactions; prevents all anomalies.
    snapshot_isolation [database_transaction_isolation_and_concurrency_c]: An isolation_level using mvcc where a transaction reads from a consistent snapshot taken at transaction start; prevents lost_update but allows write_skew.
    atomicity [database_transaction_isolation_and_concurrency_c]: The all-or-nothing property: a transaction's effects are either fully applied or fully absent; implemented via undo_log and transaction rollback.
      observation_window [deep_isolation_level]: The temporal scope during which a reading transaction may see uncommitted changes from other transactions, bounded by those transactions' commit operations.
      all_or_nothing [deep_database_transaction]: The conceptual guarantee that a transaction executes as an indivisible unit: either every operation succeeds or no operation has any effect.
      commit [database_transaction_isolation_and_concurrency_c]: The act of making a transaction's effects permanent: flush log records to durable storage, release locks, transition transaction_state to committed.
      rollback [database_transaction_isolation_and_concurrency_c]: The act of undoing a transaction's effects using undo_log entries, returning the database to its pre-transaction state.
      transaction_log [database_transaction_isolation_and_concurrency_c]: An append-only sequence of records tracking every change made by transactions; the primary mechanism for atomicity and durability.
      transaction_state [database_transaction_isolation_and_concurrency_c]: The current phase of a transaction lifecycle: active, partially_committed, committed, aborted; drives lock release and recovery behavior.
      undo_log [database_transaction_isolation_and_concurrency_c]: Log records describing the previous state of modified data; used to undo uncommitted transaction changes during rollback and recovery.
      write_ahead_logging [database_transaction_isolation_and_concurrency_c]: A protocol requiring log records be flushed to durable storage before the corresponding data changes are applied; ensures durability and atomicity.
        partial_state_prevention [deep_database_transaction]: The enforcement mechanism ensuring that if a transaction fails at any point before transaction_boundary, no tuple modifications leak into committed_data; achieved by deferring all visible effects until commit.
        aborted_state [database_transaction_isolation_and_concurrency_c]: The terminal transaction_state after rollback completes; all acquired locks are released and the transaction cannot be restarted automatically.
        committed [database_transaction_isolation_and_concurrency_c]: The terminal transaction_state after durable persistence of all changes; locks are released per locking_protocol rules.
        before_image [deep_database_transaction]: The committed database state of a row immediately before a transaction modifies it; recorded in the undo_log so the modification can be undone if the transaction rolls back.
        compensation_action [deep_database_transaction]: A corrective operation executed when forward undo via undo_log is impossible; used in distributed systems where original transaction steps cannot be directly reversed, preserving atomicity through logically equivalent alternatives.
        transaction_boundary [deep_database_transaction]: The demarcation point between consecutive transaction executions defining the scope over which atomicity applies; all effects within are committed or none are, with no partial visibility across the boundary.

YOUR JOB: define this territory ONE LEVEL OF GRANULARITY DEEPER than it currently is. Name the parts inside the parts. Every claim you emit is proof-checked; incoherence returns as named residue — repair it exactly. You never invent formats: emit exactly the JSONL construction schema you are given.
