---
name: 0.7.4-understand-base_delay
description: [0.7.4] Initial wait time in nanoseconds or microseconds before the first lock acquisition retry; the starting point o
---

# understand-base_delay

**CALL NUMBER:** `deep_spinlock.base_delay : deep_exponential_backoff(4)`
**DEFINITION:** Initial wait time in nanoseconds or microseconds before the first lock acquisition retry; the starting point of the exponential schedule.

Invoke this skill to understand `base_delay` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_exponential_backoff`
- **djt_min_delay** (d1): Lower bound of the uniform sampling range in decorrelated jitter; typically derived from base_delay and serves as the floor below which no wait interval may fall, ensuring at least a minimal pause before retry.
- **djt_bounding_range** (d2): The closed interval [min_delay, previous_delay times decorrelation_factor] from which the uniform random sample is drawn to compute the next current_delay; bounds the worst-case wait while allowing history-dependent growth.
- **djt_random_uniform_sample** (d3): The uniform random draw within the bounding range that produces the new current_delay value; the randomness decorrelates this thread's retry timing from concurrent threads.
- **djt_wave_attenuation** (d4): The emergent property that decorrelated jitter reduces the probability of simultaneous retries among competing threads; achieved through per-thread history-dependent ranges that diverge over time.

## CONSUMERS (what needs this)
`current_delay`, `exponential_backoff`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (407 concepts / 477 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
