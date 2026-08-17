---
name: 0.6.1-understand-rmw_ind_001
description: [0.6.1] rmw_operation: an atomic fetch_add, fetch_sub, fetch_or, fetch_and, fetch_xor, fetch_max, fetch_min, or fetch_
---

# understand-rmw_ind_001

**CALL NUMBER:** `deep_indivisibility_prope.rmw_ind_001 : deep_c11_memory_model(3)`
**DEFINITION:** rmw_operation: an atomic fetch_add, fetch_sub, fetch_or, fetch_and, fetch_xor, fetch_max, fetch_min, or fetch_compare_exchange on a C11 atomic variable; the operation atomically reads the current value, computes a new value, and writes it back as a single hardware-level instruction sequence.

Invoke this skill to understand `rmw_ind_001` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_c11_memory_model`
- **load_indivisibility** (d2): A relaxed atomic load returns exactly one value from the modification order of the target variable; no torn read of a partial value encoded in fewer bits than the atomic word is possible.
- **store_indivisibility** (d2): A relaxed atomic store writes the complete value as one indivisible step; no intermediate write of a partial value encoded in fewer bits than the atomic word is observable by any thread.
- **no_tearing_guarantee** (d3): The guarantee that multi-byte atomic values cannot be observed in a torn state where some bytes reflect the old value and others reflect a new concurrent value.

### from `deep_indivisibility_prope`
- **rmw_ind_002** (d1): read_phase: the initial observation step of an RMW operation wherein the current value of the atomic variable is captured from the modification order; this value is returned as the operation's result for fetch variants or used as input to the modification computation.
- **rmw_ind_003** (d1): modify_phase: the purely computational step wherein the value captured in the read phase is transformed by the operation's specific function (addition, subtraction, bitwise OR, bitwise AND, exclusive OR, maximum, minimum, or conditional replacement); this phase produces the value to be written but does not interact with memory.
- **rmw_ind_004** (d1): write_phase: the final step wherein the result of the modify phase is written atomically to the target variable; this write becomes the new current value visible in the modification order for all subsequent operations.
- **rmw_ind_005** (d1): no_intermediate_visibility: the constraint that no thread can observe the atomic variable in a state that reflects only the read_phase result or only a partial write; the variable appears unchanged until the write_phase completes, at which point it reflects the complete new value.
- **rmw_ind_006** (d1): modification_order_commitment: the serialization of the RMW operation into the global modification order of the target atomic variable at the instant the write_phase becomes visible; this ordering point determines the value returned by concurrent operations.
- **rmw_ind_007** (d1): relaxed_rmw_semantics: RMW operations under memory_order_relaxed still provide indivisibility guarantees even though they impose no synchronization or ordering constraints with respect to other memory accesses; the atomicity property is independent of the memory ordering property.
- **rmw_ind_008** (d1): fetch_return_value: the value returned by a fetch_* operation, which is always the value observed during the read_phase before the modification was applied; this semantics distinguishes fetch_add from fetch_add_return or similar variants.
- **rmw_ind_009** (d1): compare_exchange_indivisibility: the CAS operation performs an atomic compare of the observed value against an expected value and conditionally performs the write_phase only if the comparison succeeds; the compare and the conditional write constitute a single indivisible check-and-set operation.

## CONSUMERS (what needs this)
`rmw_ind_000`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (407 concepts / 477 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
