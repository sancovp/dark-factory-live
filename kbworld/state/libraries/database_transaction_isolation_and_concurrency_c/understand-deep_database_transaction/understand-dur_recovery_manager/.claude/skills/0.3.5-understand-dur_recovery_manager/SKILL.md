---
name: 0.3.5-understand-dur_recovery_manager
description: [0.3.5] The subsystem that enforces durability by reconstructing the committed database state from transaction_log aft
---

# understand-dur_recovery_manager

**CALL NUMBER:** `deep_database_transaction.dur_recovery_manager`
**DEFINITION:** The subsystem that enforces durability by reconstructing the committed database state from transaction_log after a crash; scans log forward to redo committed changes and backward to undo uncommitted ones.

Invoke this skill to understand `dur_recovery_manager` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_database_transaction`
- **dur_redo_log** (d1): Log records describing the after-image of modified data; during recovery the manager reapplies these records to restore committed transaction effects.
- **dur_undo_log** (d1): Log records describing the before-image of modified data; used during rollback and recovery to reverse uncommitted changes, preserving durability by ensuring only committed effects survive.
- **dur_write_ahead_logging** (d1): A protocol mandating that log records describing modifications be flushed to durable_storage before the corresponding data pages are written to disk; foundational mechanism for both atomicity and durability.
- **dur_log_flush** (d2): The synchronous I/O operation that transfers log buffers from volatile memory to durable_storage; must complete before commit returns success to the client.
- **dur_durable_storage** (d3): The physical medium or storage subsystem that guarantees bitwise persistence of written data across power loss, hardware failure, and system crashes; the endpoint of all durability guarantees.

## CONSUMERS (what needs this)
`dur_crash_recovery`, `recovery_manager`

---
*Projected from the `database transaction isolation and concurrency control` KB (280 concepts / 214 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
