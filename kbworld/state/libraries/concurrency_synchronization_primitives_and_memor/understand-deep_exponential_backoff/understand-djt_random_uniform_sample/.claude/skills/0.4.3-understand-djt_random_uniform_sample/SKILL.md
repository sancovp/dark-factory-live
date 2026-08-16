---
name: 0.4.3-understand-djt_random_uniform_sample
description: [0.4.3] The uniform random draw within the bounding range that produces the new current_delay value; the randomness de
---

# understand-djt_random_uniform_sample

**CALL NUMBER:** `deep_exponential_backoff.djt_random_uniform_sample`
**DEFINITION:** The uniform random draw within the bounding range that produces the new current_delay value; the randomness decorrelates this thread's retry timing from concurrent threads.

Invoke this skill to understand `djt_random_uniform_sample` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_exponential_backoff`
- **djt_wave_attenuation** (d1): The emergent property that decorrelated jitter reduces the probability of simultaneous retries among competing threads; achieved through per-thread history-dependent ranges that diverge over time.

## CONSUMERS (what needs this)
`djt_bounding_range`, `jitter`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (377 concepts / 413 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
