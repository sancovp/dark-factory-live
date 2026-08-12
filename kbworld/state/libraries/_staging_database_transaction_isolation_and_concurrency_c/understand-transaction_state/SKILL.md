# understand-transaction_state

**CALL NUMBER:** `database_transaction_isolation_and_concurrency_c.transaction_state : deep_isolation_level(1)`
**DEFINITION:** The current phase of a transaction lifecycle: active, partially_committed, committed, aborted; drives lock release and recovery behavior.

Invoke this skill to understand `transaction_state` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `database_transaction_isolation_and_concurrency_c`
- **aborted_state** (d1): The terminal transaction_state after rollback completes; all acquired locks are released and the transaction cannot be restarted automatically.
- **committed** (d1): The terminal transaction_state after durable persistence of all changes; locks are released per locking_protocol rules.

### from `deep_isolation_level`
- **committed_data** (d2): database state resulting from successfully completed transactions; constitutes the visible universe for read_committed queries

## CONSUMERS (what needs this)
`active_state`, `atomicity`, `commit`, `rollback`

---
*Projected from the `database transaction isolation and concurrency control` KB (217 concepts / 124 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*