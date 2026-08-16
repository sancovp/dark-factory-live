---
name: 0.4.2-understand-commit_visibility_boundary
description: "[0.4.2] temporal threshold in read_committed: a datum is visible iff its committing_transaction committed before the r"
---

# understand-commit_visibility_boundary

**CALL NUMBER:** `deep_isolation_level.commit_visibility_boundary`
**DEFINITION:** temporal threshold in read_committed: a datum is visible iff its committing_transaction committed before the reading statement started

Invoke this skill to understand `commit_visibility_boundary` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_isolation_level`
- **committed_data** (d1): database state resulting from successfully completed transactions; constitutes the visible universe for read_committed queries
- **statement_start_timestamp** (d1): logical moment recorded when each statement begins, establishing the visibility cutoff point for read_committed row versions

## CONSUMERS (what needs this)
`no_dirty_reads`, `statement_level_read_consistency`

---
*Projected from the `database transaction isolation and concurrency control` KB (280 concepts / 214 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
