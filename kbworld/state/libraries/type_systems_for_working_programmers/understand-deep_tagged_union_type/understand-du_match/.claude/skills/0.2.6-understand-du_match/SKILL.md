---
name: 0.2.6-understand-du_match
description: [0.2.6] The elimination form: a function that, given a discriminated union value, dispatches on its du_tag to apply th
---

# understand-du_match

**CALL NUMBER:** `deep_tagged_union_type.du_match`
**DEFINITION:** The elimination form: a function that, given a discriminated union value, dispatches on its du_tag to apply the appropriate handler to the du_payload, yielding a uniform result type.

Invoke this skill to understand `du_match` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_tagged_union_type`
- **du_payload** (d1): The data value carried by a specific variant of a discriminated union. Only one payload is live at a time; the tag selects which one.
- **du_tag** (d1): A value-level or type-level label that uniquely identifies which variant of a discriminated union is active in a given value. The tag is the first-class evidence of variant membership.

## CONSUMERS (what needs this)
`discriminated_union`, `du_exhaustiveness`

---
*Projected from the `type systems for working programmers` KB (242 concepts / 186 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
