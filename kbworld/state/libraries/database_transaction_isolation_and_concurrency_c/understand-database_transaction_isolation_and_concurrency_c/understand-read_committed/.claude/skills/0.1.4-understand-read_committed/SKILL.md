---
name: 0.1.4-understand-read_committed
description: [0.1.4] An isolation_level where each statement sees only data committed before that statement begins; prevents dirty_
---

# understand-read_committed

**CALL NUMBER:** `database_transaction_isolation_and_concurrency_c.read_committed : deep_database_transaction(6), deep_isolation_level(4)`
**DEFINITION:** An isolation_level where each statement sees only data committed before that statement begins; prevents dirty_read but allows non_repeatable_read and phantom_read.

Invoke this skill to understand `read_committed` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `database_transaction_isolation_and_concurrency_c`
- **dirty_read** (d1): An anomaly where a transaction reads data written by another transaction that has not yet committed; only possible in read_uncommitted.
- **isolation_level** (d1): A configurable parameter defining the degree to which concurrent transactions are isolated from each other's uncommitted or intermediate effects.
- **non_repeatable_read** (d1): An anomaly where a transaction reads the same row twice and gets different values because another transaction modified and committed between reads.
- **phantom_read** (d1): An anomaly where a transaction re-executes a range query and gets a different set of rows due to another transaction inserting or deleting rows in that range.
- **read_uncommitted** (d2): The weakest isolation_level: transactions may observe uncommitted changes from other transactions, permitting dirty_read.
- **repeatable_read** (d2): An isolation_level ensuring that all reads within a transaction see a consistent snapshot as of transaction start; prevents non_repeatable_read but may permit phantom_read.
- **serializable** (d2): The strongest isolation_level: the result of executing concurrent transactions is equivalent to some serial order of those transactions; prevents all anomalies.
- **snapshot_isolation** (d2): An isolation_level using mvcc where a transaction reads from a consistent snapshot taken at transaction start; prevents lost_update but allows write_skew.
- **atomicity** (d2): The all-or-nothing property: a transaction's effects are either fully applied or fully absent; implemented via undo_log and transaction rollback.
- **commit** (d3): The act of making a transaction's effects permanent: flush log records to durable storage, release locks, transition transaction_state to committed.
- **rollback** (d3): The act of undoing a transaction's effects using undo_log entries, returning the database to its pre-transaction state.
- **transaction_log** (d3): An append-only sequence of records tracking every change made by transactions; the primary mechanism for atomicity and durability.
- **transaction_state** (d3): The current phase of a transaction lifecycle: active, partially_committed, committed, aborted; drives lock release and recovery behavior.
- **undo_log** (d3): Log records describing the previous state of modified data; used to undo uncommitted transaction changes during rollback and recovery.
- **write_ahead_logging** (d3): A protocol requiring log records be flushed to durable storage before the corresponding data changes are applied; ensures durability and atomicity.
- **aborted_state** (d4): The terminal transaction_state after rollback completes; all acquired locks are released and the transaction cannot be restarted automatically.
- **committed** (d4): The terminal transaction_state after durable persistence of all changes; locks are released per locking_protocol rules.

### from `deep_database_transaction`
- **statement** (d1): A single SQL operation within a transaction; atomicity requires that each statement either fully completes its effect or fully reverts before the next statement begins.
- **all_or_nothing** (d3): The conceptual guarantee that a transaction executes as an indivisible unit: either every operation succeeds or no operation has any effect.
- **partial_state_prevention** (d4): The enforcement mechanism ensuring that if a transaction fails at any point before transaction_boundary, no tuple modifications leak into committed_data; achieved by deferring all visible effects until commit.
- **before_image** (d4): The committed database state of a row immediately before a transaction modifies it; recorded in the undo_log so the modification can be undone if the transaction rolls back.
- **compensation_action** (d4): A corrective operation executed when forward undo via undo_log is impossible; used in distributed systems where original transaction steps cannot be directly reversed, preserving atomicity through logically equivalent alternatives.
- **transaction_boundary** (d5): The demarcation point between consecutive transaction executions defining the scope over which atomicity applies; all effects within are committed or none are, with no partial visibility across the boundary.

### from `deep_isolation_level`
- **committed_data** (d1): database state resulting from successfully completed transactions; constitutes the visible universe for read_committed queries
- **transaction_read** (d2): The act of a transaction executing a read operation; at read_uncommitted this read may return uncommitted_change from concurrent transactions.
- **uncommitted_change** (d2): A modification to database state made by a transaction that has not yet committed; visible to other transactions at read_uncommitted.
- **observation_window** (d3): The temporal scope during which a reading transaction may see uncommitted changes from other transactions, bounded by those transactions' commit operations.

## CONSUMERS (what needs this)
`isolation_level`

---
*Projected from the `database transaction isolation and concurrency control` KB (217 concepts / 124 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
