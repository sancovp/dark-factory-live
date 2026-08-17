# understand-thundering_herd_retry_coordination

**CALL NUMBER:** `deep_exponential_backoff.thundering_herd_retry_coordination`
**DEFINITION:** The phenomenon where concurrently woken threads retry a failing operation in near-lockstep, reinforcing the contention surge; mitigated by jitter applied to retry delays.

Invoke this skill to understand `thundering_herd_retry_coordination` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

## CONSUMERS (what needs this)
`thundering_herd_backoff_adaptation`, `thundering_herd_contention_surge`, `thundering_herd_jitter_decorrelation`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (407 concepts / 477 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*