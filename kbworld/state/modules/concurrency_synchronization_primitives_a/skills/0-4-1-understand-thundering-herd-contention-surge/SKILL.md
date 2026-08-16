---
name: 0.4.1-understand-thundering_herd_contention_surge
description: "[0.4.1] A transient spike in the rate of lock or resource acquisition attempts triggered by mass wakeup, producing que"
---

# understand-thundering_herd_contention_surge

**CALL NUMBER:** `deep_exponential_backoff.thundering_herd_contention_surge`
**DEFINITION:** A transient spike in the rate of lock or resource acquisition attempts triggered by mass wakeup, producing queue buildup and wasted retry cycles.

Invoke this skill to understand `thundering_herd_contention_surge` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_exponential_backoff`
- **thundering_herd_fairness_starvation** (d1): A degraded thread fairness condition where some members of the wait_set are repeatedly overtaken by newly arriving competitors, never acquiring the resource despite eligibility.
- **thundering_herd_retry_coordination** (d1): The phenomenon where concurrently woken threads retry a failing operation in near-lockstep, reinforcing the contention surge; mitigated by jitter applied to retry delays.

## CONSUMERS (what needs this)
`thundering_herd_phased_awakening`, `thundering_herd_spurious_wakeup`, `thundering_herd_wait_queue_depth`, `thundering_herd_wake_one_semantics`, `thundering_herd_wakeup_ratio`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (377 concepts / 413 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
