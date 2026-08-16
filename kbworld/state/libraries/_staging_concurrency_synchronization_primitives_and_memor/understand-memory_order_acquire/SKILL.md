# understand-memory_order_acquire

**CALL NUMBER:** `deep_synchronizes_with.memory_order_acquire : deep_happens_before_relat(5)`
**DEFINITION:** Memory ordering barrier ensuring all loads and stores after the barrier in program order cannot be reordered before it, synchronizing with release stores.

Invoke this skill to understand `memory_order_acquire` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_happens_before_relat`
- **acquire_fence** (d1): A memory ordering primitive that ensures all load and store operations appearing after the fence in program order do not begin until the fence completes and all prior writes are visible.
- **synchronizes_with_acquire_side** (d2): The acquire-side endpoint of a synchronizes_with relation: an atomic operation or fence that performs an acquire action, making all subsequently observed writes visible to the acquiring thread.
- **program_order** (d3): The sequential ordering of operations within a single thread as written in the source code, before any concurrent interleaving is considered.
- **inter_thread_happens_before** (d4): The subset of happens_before relations that cross thread boundaries, established by synchronizes_with connections between release and acquire operations.
- **happens_before_order** (d5): A transitive, irreflexive partial order over operations in a memory model that defines which operations must appear to precede others from any thread's perspective.

## CONSUMERS (what needs this)
`atomic_load`, `c11_atomic`, `mcs_lock`, `memory_order_consume`, `synchronizes_with`

---
*Projected from the `concurrency synchronization primitives and memory models` KB (377 concepts / 413 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*