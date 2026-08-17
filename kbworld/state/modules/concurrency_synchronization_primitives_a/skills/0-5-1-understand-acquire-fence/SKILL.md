---
name: 0.5.1-understand-acquire_fence
description: "[0.5.1] A memory ordering primitive that ensures all load and store operations appearing after the fence in program or"
---

# understand-acquire_fence

**CALL NUMBER:** `deep_happens_before_relat.acquire_fence`
**DEFINITION:** A memory ordering primitive that ensures all load and store operations appearing after the fence in program order do not begin until the fence completes and all prior writes are visible.

Invoke this skill to understand `acquire_fence` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_happens_before_relat`
- **synchronizes_with_acquire_side** (d1): The acquire-side endpoint of a synchronizes_with relation: an atomic operation or fence that performs an acquire action, making all subsequently observed writes visible to the acquiring thread.
- **program_order** (d2): The sequential ordering of operations within a single thread as written in the source code, before any concurrent interleaving is considered.
- **inter_thread_happens_before** (d3): The subset of happens_before relations that cross thread boundaries, established by synchronizes_with connections between release and acquire operations.
- **happens_before_order** (d4): A transitive, irreflexive partial order over operations in a memory model that defines which operations must appear to precede others from any thread's perspective.

## CONSUMERS (what needs this)
`arm_dmb`, `atomic_fence`, `memory_order_acquire`, `sw_acquire_fence`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (407 concepts / 477 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
