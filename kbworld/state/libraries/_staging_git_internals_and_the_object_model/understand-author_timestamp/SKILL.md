# understand-author_timestamp

**CALL NUMBER:** `deep_commit_object.author_timestamp`
**DEFINITION:** Integer Unix timestamp recording when the author created the change; represents seconds since epoch (1970-01-01 00:00:00 UTC) in the author field.

Invoke this skill to understand `author_timestamp` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_commit_object`
- **author_date** (d1): Composite of author_timestamp and author_timezone; git log --date= formats this value.

## CONSUMERS (what needs this)
`author_date`, `author_timezone`

---
*Projected from the `git internals and the object model` KB (162 concepts / 159 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*