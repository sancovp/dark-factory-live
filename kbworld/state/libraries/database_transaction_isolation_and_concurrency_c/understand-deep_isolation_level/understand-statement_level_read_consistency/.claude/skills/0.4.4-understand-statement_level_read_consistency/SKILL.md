---
name: 0.4.4-understand-statement_level_read_consistency
description: [0.4.4] guarantee within read_committed that each SQL statement sees all changes committed at the moment that statemen
---

# understand-statement_level_read_consistency

**CALL NUMBER:** `deep_isolation_level.statement_level_read_consistency`
**DEFINITION:** guarantee within read_committed that each SQL statement sees all changes committed at the moment that statement began execution

Invoke this skill to understand `statement_level_read_consistency` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_isolation_level`
- **commit_visibility_boundary** (d1): temporal threshold in read_committed: a datum is visible iff its committing_transaction committed before the reading statement started
- **statement_start_timestamp** (d1): logical moment recorded when each statement begins, establishing the visibility cutoff point for read_committed row versions
- **committed_data** (d2): database state resulting from successfully completed transactions; constitutes the visible universe for read_committed queries

## CONSUMERS (what needs this)
`phantom_read_possible`

---
*Projected from the `database transaction isolation and concurrency control` KB (280 concepts / 214 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
