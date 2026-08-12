---
name: 0.2.6-understand-author_date
description: [0.2.6] Composite of author_timestamp and author_timezone; git log --date= formats this value.
---

# understand-author_date

**CALL NUMBER:** `deep_commit_object.author_date`
**DEFINITION:** Composite of author_timestamp and author_timezone; git log --date= formats this value.

Invoke this skill to understand `author_date` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_commit_object`
- **author_timestamp** (d1): Integer Unix timestamp recording when the author created the change; represents seconds since epoch (1970-01-01 00:00:00 UTC) in the author field.

## CONSUMERS (what needs this)
`author_timestamp`

---
*Projected from the `git internals and the object model` KB (162 concepts / 159 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
