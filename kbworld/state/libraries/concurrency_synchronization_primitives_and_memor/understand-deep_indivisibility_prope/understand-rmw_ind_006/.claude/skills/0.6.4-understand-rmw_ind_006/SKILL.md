---
name: 0.6.4-understand-rmw_ind_006
description: [0.6.4] modification_order_commitment: the serialization of the RMW operation into the global modification order of th
---

# understand-rmw_ind_006

**CALL NUMBER:** `deep_indivisibility_prope.rmw_ind_006 : deep_c11_memory_model(3)`
**DEFINITION:** modification_order_commitment: the serialization of the RMW operation into the global modification order of the target atomic variable at the instant the write_phase becomes visible; this ordering point determines the value returned by concurrent operations.

Invoke this skill to understand `rmw_ind_006` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_c11_memory_model`
- **load_indivisibility** (d1): A relaxed atomic load returns exactly one value from the modification order of the target variable; no torn read of a partial value encoded in fewer bits than the atomic word is possible.
- **store_indivisibility** (d1): A relaxed atomic store writes the complete value as one indivisible step; no intermediate write of a partial value encoded in fewer bits than the atomic word is observable by any thread.
- **no_tearing_guarantee** (d2): The guarantee that multi-byte atomic values cannot be observed in a torn state where some bytes reflect the old value and others reflect a new concurrent value.

## CONSUMERS (what needs this)
`rmw_ind_001`, `rmw_ind_004`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (407 concepts / 477 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
