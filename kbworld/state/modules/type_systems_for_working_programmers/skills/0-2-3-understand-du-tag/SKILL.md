---
name: 0.2.3-understand-du_tag
description: "[0.2.3] A value-level or type-level label that uniquely identifies which variant of a discriminated union is active in"
---

# understand-du_tag

**CALL NUMBER:** `deep_tagged_union_type.du_tag`
**DEFINITION:** A value-level or type-level label that uniquely identifies which variant of a discriminated union is active in a given value. The tag is the first-class evidence of variant membership.

Invoke this skill to understand `du_tag` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_tagged_union_type`
- **du_payload** (d1): The data value carried by a specific variant of a discriminated union. Only one payload is live at a time; the tag selects which one.

## CONSUMERS (what needs this)
`du_closed`, `du_match`, `du_open`, `du_variant`, `prism_builder`, `prism_matcher`

---
*Projected from the `type systems for working programmers` KB (242 concepts / 186 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
