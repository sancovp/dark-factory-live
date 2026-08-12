# understand-cache_invalidation

**CALL NUMBER:** `resilience_and_reliability_engineering_patterns.cache_invalidation`
**DEFINITION:** removing stale cached entries; must be timely to prevent serving incorrect data

Invoke this skill to understand `cache_invalidation` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `resilience_and_reliability_engineering_patterns`
- **cache_stampede** (d1): concurrent cache misses causing thundering herd on backend; mitigated by probabilistic early expiration

## CONSUMERS (what needs this)
`cache_aside`

---
*Projected from the `resilience and reliability engineering patterns` KB (118 concepts / 34 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*