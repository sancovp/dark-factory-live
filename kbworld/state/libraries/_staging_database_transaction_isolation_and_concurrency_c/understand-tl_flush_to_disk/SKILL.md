# understand-tl_flush_to_disk

**CALL NUMBER:** `deep_database_transaction.tl_flush_to_disk`
**DEFINITION:** The act of transferring the contents of tl_log_buffer to durable storage; triggered by transaction commit, tl_log_buffer overflow, or a periodic checkpoint; O(1) or O(n) bounded by buffer size.

Invoke this skill to understand `tl_flush_to_disk` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_database_transaction`
- **tl_dirty_page_table** (d1): A runtime data structure maintained by recovery_manager listing data pages modified but not yet flushed; consulted during checkpoint to ensure write_ahead_logging invariants hold.

## CONSUMERS (what needs this)
`tl_commit_record`, `tl_wal_protocol`

---
*Projected from the `database transaction isolation and concurrency control` KB (217 concepts / 124 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*