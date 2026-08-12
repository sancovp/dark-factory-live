---
name: 0.2.1-understand-circuit_breaker
description: [0.2.1] pattern preventing cascading failures by stopping calls to failing service; trips open on threshold violations
---

# understand-circuit_breaker

**CALL NUMBER:** `resilience_and_reliability_engineering_patterns.circuit_breaker`
**DEFINITION:** pattern preventing cascading failures by stopping calls to failing service; trips open on threshold violations

Invoke this skill to understand `circuit_breaker` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `resilience_and_reliability_engineering_patterns`
- **cascading_failure** (d1): failure propagation from one component to others; circuit breakers and bulkheads prevent this

## CONSUMERS (what needs this)
`circuit_breaker_half_open_limit`, `circuit_breaker_state_closed`, `circuit_breaker_state_half_open`, `circuit_breaker_state_open`

---
*Projected from the `resilience and reliability engineering patterns` KB (118 concepts / 34 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
