---
name: 0.2.5-understand-author_name
description: [0.2.5] String component of the author field in a commit object specifying the primary creator's display name; appears
---

# understand-author_name

**CALL NUMBER:** `deep_commit_object.author_name : git_internals_and_the_object_model(1)`
**DEFINITION:** String component of the author field in a commit object specifying the primary creator's display name; appears before the email in the standard <name> <email> format.

Invoke this skill to understand `author_name` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `git_internals_and_the_object_model`
- **author_field** (d1): Name and email in commit object identifying primary creator; distinct from committer who applied the patch.

## CONSUMERS (what needs this)
`author_identification`

---
*Projected from the `git internals and the object model` KB (162 concepts / 159 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
