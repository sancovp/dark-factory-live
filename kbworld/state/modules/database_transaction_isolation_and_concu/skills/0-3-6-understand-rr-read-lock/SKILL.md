---
name: 0.3.6-understand-rr_read_lock
description: "[0.3.6] A shared_lock acquired when a row is read under repeatable_read; held until transaction commits or rolls back,"
---

# understand-rr_read_lock

**CALL NUMBER:** `deep_database_transaction.rr_read_lock`
**DEFINITION:** A shared_lock acquired when a row is read under repeatable_read; held until transaction commits or rolls back, preventing any concurrent transaction from acquiring a write_lock on that row.

Invoke this skill to understand `rr_read_lock` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **rr_write_ahead_logging** (d1): The write_ahead_logging requirement within a lock-based repeatable_read system mandating that every recovery_log_entry be flushed to durable storage before the corresponding row modification is applied, ensuring crash recovery can reconstruct all transaction effects exactly once.
- **rr_commit** (d2): The commit event in a transaction executing under repeatable_read, marking the transaction_boundary at which all held rr_read_locks undergo lock_release and the transaction's effects become durable and visible to other transactions under the same isolation level.
- **rr_rollback** (d2): The rollback operation executed by a transaction under repeatable_read, undoing all row modifications using recovery_log_entry before_image data, releasing all held rr_read_locks via lock_release, and transitioning the rr_transaction_state to aborted.
- **rr_transaction_state** (d2): The phase of a transaction executing under repeatable_read, following the standard transaction_state lifecycle of active, partially_committed, committed, or aborted, where each phase drives whether rr_read_locks are held or released.

### from `deep_database_transaction`
- **rr_lock_duration** (d1): The temporal scope from row_read acquisition of read_lock until transaction_boundary where atomicity resolves via commit or rollback, releasing all held locks.
- **rr_non_repeatable_read_prevention** (d1): The guarantee that repeating the same row read within a transaction always returns the same before_image; achieved by holding read_lock preventing concurrent write_lock acquisition.
- **rr_write_lock_prevention** (d1): A write_lock request on a row already held with a read_lock by another transaction blocks until that transaction releases its locks at commit or rollback.
- **rr_lock_timeout** (d2): A mechanism to prevent indefinite blocking when write_lock acquisition is stalled by read_locks held under repeatable_read; transaction rolls back if lock not acquired within threshold.

## CONSUMERS (what needs this)
`rr_definition`

---
*Projected from the `database transaction isolation and concurrency control` KB (280 concepts / 214 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
