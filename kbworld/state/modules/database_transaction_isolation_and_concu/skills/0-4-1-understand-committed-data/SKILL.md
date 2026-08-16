---
name: 0.4.1-understand-committed_data
description: "[0.4.1] database state resulting from successfully completed transactions; constitutes the visible universe for read_c"
---

# understand-committed_data

**CALL NUMBER:** `deep_isolation_level.committed_data`
**DEFINITION:** database state resulting from successfully completed transactions; constitutes the visible universe for read_committed queries

Invoke this skill to understand `committed_data` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

## CONSUMERS (what needs this)
`aborted_data`, `c004`, `c005`, `c011`, `commit_visibility_boundary`, `committed`, `read_committed`, `write_lock_held_until_commit`

---
*Projected from the `database transaction isolation and concurrency control` KB (280 concepts / 214 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
