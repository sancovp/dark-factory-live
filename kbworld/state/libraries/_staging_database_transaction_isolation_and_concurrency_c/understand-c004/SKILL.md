# understand-c004

**CALL NUMBER:** `deep_rollback.c004 : deep_isolation_level(1)`
**DEFINITION:** commit durability: the guaranteed persistence property that all writes of a committed transaction survive system crashes; realized via write-ahead log

Invoke this skill to understand `c004` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_isolation_level`
- **committed_data** (d1): database state resulting from successfully completed transactions; constitutes the visible universe for read_committed queries

### from `deep_rollback`
- **c009** (d1): commit completion: the terminal state transition from active to committed; releases all locks held exclusively and schedules release of shared locks per protocol
- **c003** (d2): commit sequence number (CSN): a monotonically incrementing identifier assigned to each committed transaction; provides total ordering of committed state changes
- **c008** (d2): commit acknowledgment: the confirmation signal returned to the client indicating successful durable persistence of the transaction
- **c010** (d2): commit promise: the contractual guarantee to the user that transaction effects are durable and will survive any subsequent system restart

---
*Projected from the `database transaction isolation and concurrency control` KB (280 concepts / 214 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*