---
name: 0.2.4-understand-du_payload
description: "[0.2.4] The data value carried by a specific variant of a discriminated union. Only one payload is live at a time; the"
---

# understand-du_payload

**CALL NUMBER:** `deep_tagged_union_type.du_payload`
**DEFINITION:** The data value carried by a specific variant of a discriminated union. Only one payload is live at a time; the tag selects which one.

Invoke this skill to understand `du_payload` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

## CONSUMERS (what needs this)
`du_match`, `du_tag`, `du_variant`, `lens_getter`, `lens_setter`

---
*Projected from the `type systems for working programmers` KB (242 concepts / 186 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
