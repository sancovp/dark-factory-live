---
name: 0.5.1-understand-jitter
description: [0.5.1] Randomized variance introduced into the computed delay to decorrelate competing threads and mitigate thunderin
---

# understand-jitter

**CALL NUMBER:** `deep_spinlock.jitter : deep_exponential_backoff(2)`
**DEFINITION:** Randomized variance introduced into the computed delay to decorrelate competing threads and mitigate thundering-herd synchronization on lock release.

Invoke this skill to understand `jitter` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_exponential_backoff`
- **djt_random_uniform_sample** (d1): The uniform random draw within the bounding range that produces the new current_delay value; the randomness decorrelates this thread's retry timing from concurrent threads.
- **djt_wave_attenuation** (d2): The emergent property that decorrelated jitter reduces the probability of simultaneous retries among competing threads; achieved through per-thread history-dependent ranges that diverge over time.

### from `deep_spinlock`
- **decorrelated_jitter** (d1): Jitter strategy where each thread computes delay = random.uniform(min_delay, previous_delay * 3); history-dependent decorrelation reduces coordinated retry waves.
- **equal_jitter** (d1): Jitter strategy computing delay = base_delay / 2 + random.uniform(0, base_delay / 2); ensures wait never falls below half the nominal delay.
- **full_jitter** (d1): Jitter strategy selecting a uniform random value in the range [0, current_delay]; maximizes desynchronization at the cost of potentially very short waits.

## CONSUMERS (what needs this)
`exponential_backoff`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (211 concepts / 207 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
