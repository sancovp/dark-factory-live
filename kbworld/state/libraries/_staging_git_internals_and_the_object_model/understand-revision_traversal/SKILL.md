# understand-revision_traversal

**CALL NUMBER:** `?.revision_traversal : git_internals_and_the_object_model(1)`
**DEFINITION:** An ordered walk over commits in git's object graph, visiting each revision reachable from one or more starting points (refs, commits) following parent links, in depth-first, breadth-first, or topological order, to collect metadata, compute reachability, or stream objects for processing.

Invoke this skill to understand `revision_traversal` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `git_internals_and_the_object_model`
- **rev_parse_extended** (d1): Extended reference syntax: HEAD~n (n-th ancestor), HEAD^n (n-th parent in merge), HEAD@{n} (reflog entry), HEAD^{type} (dereference type).

---
*Projected from the `git internals and the object model` KB (162 concepts / 159 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*