---
name: 0.4.4-understand-thundering_herd_wakeup_event
description: [0.4.4] A single signal or broadcast that causes ALL members of a wait_set to transition from blocked to runnable simu
---

# understand-thundering_herd_wakeup_event

**CALL NUMBER:** `deep_exponential_backoff.thundering_herd_wakeup_event`
**DEFINITION:** A single signal or broadcast that causes ALL members of a wait_set to transition from blocked to runnable simultaneously; the atomic cause of the thundering-herd pattern.

Invoke this skill to understand `thundering_herd_wakeup_event` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_exponential_backoff`
- **thundering_herd_wait_set** (d1): A collection of threads blocked on a single synchronization point awaiting a condition; the structural prerequisite for thundering-herd because coordinated wakeup of this set is the failure mode.
- **thundering_herd_wakeup_ratio** (d1): The ratio of awakened threads to threads that can usefully proceed; a ratio much greater than one indicates a thundering-herd inefficiency.
- **thundering_herd_wait_queue_depth** (d2): The number of threads resident in the wait_set at notification time; greater depth directly scales the severity of the thundering-herd.
- **thundering_herd_contention_surge** (d2): A transient spike in the rate of lock or resource acquisition attempts triggered by mass wakeup, producing queue buildup and wasted retry cycles.
- **thundering_herd_fairness_starvation** (d3): A degraded thread fairness condition where some members of the wait_set are repeatedly overtaken by newly arriving competitors, never acquiring the resource despite eligibility.
- **thundering_herd_retry_coordination** (d3): The phenomenon where concurrently woken threads retry a failing operation in near-lockstep, reinforcing the contention surge; mitigated by jitter applied to retry delays.

## CONSUMERS (what needs this)
`thundering_herd_backoff_adaptation`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (211 concepts / 207 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
