---
name: 0.5.4-understand-c003
description: [0.5.4] commit sequence number (CSN): a monotonically incrementing identifier assigned to each committed transaction; 
---

# understand-c003

**CALL NUMBER:** `deep_rollback.c003`
**DEFINITION:** commit sequence number (CSN): a monotonically incrementing identifier assigned to each committed transaction; provides total ordering of committed state changes

Invoke this skill to understand `c003` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_rollback`
- **c009** (d1): commit completion: the terminal state transition from active to committed; releases all locks held exclusively and schedules release of shared locks per protocol
- **c008** (d2): commit acknowledgment: the confirmation signal returned to the client indicating successful durable persistence of the transaction
- **c010** (d2): commit promise: the contractual guarantee to the user that transaction effects are durable and will survive any subsequent system restart

## CONSUMERS (what needs this)
`c009`

---
*Projected from the `database transaction isolation and concurrency control` KB (280 concepts / 214 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
