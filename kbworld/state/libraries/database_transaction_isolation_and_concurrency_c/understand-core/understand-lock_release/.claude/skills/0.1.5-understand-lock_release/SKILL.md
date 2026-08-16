---
name: 0.1.5-understand-lock_release
description: [0.1.5] The deterministic act of relinquishing every lock held by a transaction upon reaching its transaction_boundary
---

# understand-lock_release

**CALL NUMBER:** `?.lock_release`
**DEFINITION:** The deterministic act of relinquishing every lock held by a transaction upon reaching its transaction_boundary, whether through commit or abort, restoring exclusive or shared access rights to the affected rows and index entries for other transactions.

Invoke this skill to understand `lock_release` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

## CONSUMERS (what needs this)
`aborted_state`, `aborted_state_signals_lock_release`

---
*Projected from the `database transaction isolation and concurrency control` KB (280 concepts / 214 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
