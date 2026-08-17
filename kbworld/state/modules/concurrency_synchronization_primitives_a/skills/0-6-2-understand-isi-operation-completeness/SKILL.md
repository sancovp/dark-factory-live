---
name: 0.6.2-understand-isi_operation_completeness
description: "[0.6.2] The property that a relaxed atomic operation executes to full completion before any observer can witness its e"
---

# understand-isi_operation_completeness

**CALL NUMBER:** `deep_indivisibility_prope.isi_operation_completeness`
**DEFINITION:** The property that a relaxed atomic operation executes to full completion before any observer can witness its effect or lack thereof; partial execution is undetectable.

Invoke this skill to understand `isi_operation_completeness` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_indivisibility_prope`
- **isi_no_in_flight_state** (d1): The guaranteed absence of any transient value during operation execution that could be sampled by a concurrent thread; the in-flight state is logically invisible.
- **isi_post_state_visibility** (d1): The state of the target atomic variable after the operation has fully completed, which is the only alternative state an observer may witness.
- **isi_pre_state_visibility** (d1): The state of the target atomic variable as it existed before the operation commenced, which is the only alternative state an observer may witness.
- **isi_load_visibility_rule** (d2): For a relaxed atomic load, the read returns exactly one value from the modification order; no torn read of a partial encoding is observable.
- **isi_rmw_visibility_rule** (d2): For a relaxed read-modify-write operation, observers see either the complete state before the modification or the complete state after modification; the read-modify-write executes atomically without observable intermediate stages.
- **isi_store_visibility_rule** (d2): For a relaxed atomic store, any reading thread observes either the complete value that existed before the store or the complete value after the store; torn writes are impossible.
- **isi_observer_exclusivity** (d2): The constraint that any given observer of a relaxed atomic operation sees exclusively one of the two complete states; mixed or hybrid observations are prohibited.

## CONSUMERS (what needs this)
`isi_atomicity_boundary`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (407 concepts / 477 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
