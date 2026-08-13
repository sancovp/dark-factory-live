---
name: 0.4.2-understand-jitter
description: "[0.4.2] Randomized variance introduced into the computed delay to decorrelate competing threads and mitigate thunderin"
---

# understand-jitter

**CALL NUMBER:** `deep_spinlock.jitter`
**DEFINITION:** Randomized variance introduced into the computed delay to decorrelate competing threads and mitigate thundering-herd synchronization on lock release.

Invoke this skill to understand `jitter` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_spinlock`
- **decorrelated_jitter** (d1): Jitter strategy where each thread computes delay = random.uniform(min_delay, previous_delay * 3); history-dependent decorrelation reduces coordinated retry waves.
- **equal_jitter** (d1): Jitter strategy computing delay = base_delay / 2 + random.uniform(0, base_delay / 2); ensures wait never falls below half the nominal delay.
- **full_jitter** (d1): Jitter strategy selecting a uniform random value in the range [0, current_delay]; maximizes desynchronization at the cost of potentially very short waits.

## CONSUMERS (what needs this)
`exponential_backoff`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (155 concepts / 137 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
