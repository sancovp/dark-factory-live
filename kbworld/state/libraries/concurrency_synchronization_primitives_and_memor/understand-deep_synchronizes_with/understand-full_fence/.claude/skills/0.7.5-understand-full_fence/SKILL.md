---
name: 0.7.5-understand-full_fence
description: [0.7.5] A memory fence providing both acquire and release semantics; no memory operation on the issuing core may be re
---

# understand-full_fence

**CALL NUMBER:** `deep_synchronizes_with.full_fence`
**DEFINITION:** A memory fence providing both acquire and release semantics; no memory operation on the issuing core may be reordered across the fence in either direction.

Invoke this skill to understand `full_fence` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_synchronizes_with`
- **fence_synchronizes_with_fence** (d1): A pair of fences on different threads where the second fence in program order synchronizes-with the first fence establishing an ordering boundary.
- **fence_synchronizes_with_op** (d1): A relation where a fence on one thread establishes a synchronizes-with edge over an operation on another thread that accesses memory visible across the fence boundary.

## CONSUMERS (what needs this)
`arm_dmb`, `memory_order_acq_rel`, `synchronizes_with`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (377 concepts / 413 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
