---
name: 0.4.2-understand-djt_bounding_range
description: "[0.4.2] The closed interval [min_delay, previous_delay times decorrelation_factor] from which the uniform random sampl"
---

# understand-djt_bounding_range

**CALL NUMBER:** `deep_exponential_backoff.djt_bounding_range`
**DEFINITION:** The closed interval [min_delay, previous_delay times decorrelation_factor] from which the uniform random sample is drawn to compute the next current_delay; bounds the worst-case wait while allowing history-dependent growth.

Invoke this skill to understand `djt_bounding_range` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_exponential_backoff`
- **djt_random_uniform_sample** (d1): The uniform random draw within the bounding range that produces the new current_delay value; the randomness decorrelates this thread's retry timing from concurrent threads.
- **djt_wave_attenuation** (d2): The emergent property that decorrelated jitter reduces the probability of simultaneous retries among competing threads; achieved through per-thread history-dependent ranges that diverge over time.

## CONSUMERS (what needs this)
`djt_decorrelation_factor`, `djt_min_delay`, `djt_previous_delay`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (377 concepts / 413 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
