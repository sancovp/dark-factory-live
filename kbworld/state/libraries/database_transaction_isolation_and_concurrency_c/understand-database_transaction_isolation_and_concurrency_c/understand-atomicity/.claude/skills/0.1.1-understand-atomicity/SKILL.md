---
name: 0.1.1-understand-atomicity
description: [0.1.1] The all-or-nothing property: a transaction's effects are either fully applied or fully absent; implemented via
---

# understand-atomicity

**CALL NUMBER:** `database_transaction_isolation_and_concurrency_c.atomicity : deep_database_transaction(5), deep_isolation_level(1)`
**DEFINITION:** The all-or-nothing property: a transaction's effects are either fully applied or fully absent; implemented via undo_log and transaction rollback.

Invoke this skill to understand `atomicity` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `database_transaction_isolation_and_concurrency_c`
- **commit** (d1): The act of making a transaction's effects permanent: flush log records to durable storage, release locks, transition transaction_state to committed.
- **rollback** (d1): The act of undoing a transaction's effects using undo_log entries, returning the database to its pre-transaction state.
- **transaction_log** (d1): An append-only sequence of records tracking every change made by transactions; the primary mechanism for atomicity and durability.
- **transaction_state** (d1): The current phase of a transaction lifecycle: active, partially_committed, committed, aborted; drives lock release and recovery behavior.
- **undo_log** (d1): Log records describing the previous state of modified data; used to undo uncommitted transaction changes during rollback and recovery.
- **write_ahead_logging** (d1): A protocol requiring log records be flushed to durable storage before the corresponding data changes are applied; ensures durability and atomicity.
- **aborted_state** (d2): The terminal transaction_state after rollback completes; all acquired locks are released and the transaction cannot be restarted automatically.
- **committed** (d2): The terminal transaction_state after durable persistence of all changes; locks are released per locking_protocol rules.

### from `deep_database_transaction`
- **all_or_nothing** (d1): The conceptual guarantee that a transaction executes as an indivisible unit: either every operation succeeds or no operation has any effect.
- **partial_state_prevention** (d2): The enforcement mechanism ensuring that if a transaction fails at any point before transaction_boundary, no tuple modifications leak into committed_data; achieved by deferring all visible effects until commit.
- **before_image** (d2): The committed database state of a row immediately before a transaction modifies it; recorded in the undo_log so the modification can be undone if the transaction rolls back.
- **compensation_action** (d2): A corrective operation executed when forward undo via undo_log is impossible; used in distributed systems where original transaction steps cannot be directly reversed, preserving atomicity through logically equivalent alternatives.
- **transaction_boundary** (d3): The demarcation point between consecutive transaction executions defining the scope over which atomicity applies; all effects within are committed or none are, with no partial visibility across the boundary.

### from `deep_isolation_level`
- **committed_data** (d3): database state resulting from successfully completed transactions; constitutes the visible universe for read_committed queries

## CONSUMERS (what needs this)
`acid_properties`, `atomicity`, `statement`

---
*Projected from the `database transaction isolation and concurrency control` KB (217 concepts / 124 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
