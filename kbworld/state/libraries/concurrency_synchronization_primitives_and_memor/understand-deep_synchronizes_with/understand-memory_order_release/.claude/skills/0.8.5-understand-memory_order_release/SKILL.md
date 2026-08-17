---
name: 0.8.5-understand-memory_order_release
description: [0.8.5] Memory ordering barrier ensuring all loads and stores before the barrier in program order cannot be reordered 
---

# understand-memory_order_release

**CALL NUMBER:** `deep_synchronizes_with.memory_order_release : deep_happens_before_relat(6)`
**DEFINITION:** Memory ordering barrier ensuring all loads and stores before the barrier in program order cannot be reordered after it, making prior writes visible to acquiring threads.

Invoke this skill to understand `memory_order_release` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_happens_before_relat`
- **release_fence** (d1): A memory ordering primitive that ensures all load and store operations appearing before the fence in program order complete before any operations appearing after the fence begin.
- **synchronizes_with_release_side** (d2): The release-side endpoint of a synchronizes_with relation: an atomic operation or fence that performs a release action, making all prior memory operations visible to acquiring threads.
- **program_order** (d3): The sequential ordering of operations within a single thread as written in the source code, before any concurrent interleaving is considered.
- **synchronizes_with_acquire_side** (d3): The acquire-side endpoint of a synchronizes_with relation: an atomic operation or fence that performs an acquire action, making all subsequently observed writes visible to the acquiring thread.
- **inter_thread_happens_before** (d4): The subset of happens_before relations that cross thread boundaries, established by synchronizes_with connections between release and acquire operations.
- **happens_before_order** (d5): A transitive, irreflexive partial order over operations in a memory model that defines which operations must appear to precede others from any thread's perspective.

## CONSUMERS (what needs this)
`atomic_store`, `c11_atomic`, `mcs_lock`, `synchronizes_with`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (407 concepts / 477 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
