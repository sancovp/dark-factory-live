---
name: 0.5.3-understand-c002
description: [0.5.3] commit log record: the write-ahead log entry that atomically records the commit point; contains transaction id
---

# understand-c002

**CALL NUMBER:** `deep_rollback.c002`
**DEFINITION:** commit log record: the write-ahead log entry that atomically records the commit point; contains transaction identifier and commit LSN

Invoke this skill to understand `c002` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_rollback`
- **c001** (d1): commit point: the precise instant when a transaction transitions from active to committed; the log sequence number position where durable persistence is guaranteed
- **c006** (d2): commit LSN: the log sequence number position of the commit log record; the fence above which all prior transaction writes are durable
- **c009** (d2): commit completion: the terminal state transition from active to committed; releases all locks held exclusively and schedules release of shared locks per protocol
- **c003** (d3): commit sequence number (CSN): a monotonically incrementing identifier assigned to each committed transaction; provides total ordering of committed state changes
- **c008** (d3): commit acknowledgment: the confirmation signal returned to the client indicating successful durable persistence of the transaction
- **c010** (d3): commit promise: the contractual guarantee to the user that transaction effects are durable and will survive any subsequent system restart

## CONSUMERS (what needs this)
`c006`

---
*Projected from the `database transaction isolation and concurrency control` KB (280 concepts / 214 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
