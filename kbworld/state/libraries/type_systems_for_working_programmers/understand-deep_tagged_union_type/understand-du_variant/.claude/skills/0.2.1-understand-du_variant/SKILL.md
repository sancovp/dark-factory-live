---
name: 0.2.1-understand-du_variant
description: [0.2.1] A named constituent of a discriminated union, pairing a du_tag with a du_payload type. Each variant represents
---

# understand-du_variant

**CALL NUMBER:** `deep_tagged_union_type.du_variant`
**DEFINITION:** A named constituent of a discriminated union, pairing a du_tag with a du_payload type. Each variant represents one summand in the sum type.

Invoke this skill to understand `du_variant` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_tagged_union_type`
- **du_payload** (d1): The data value carried by a specific variant of a discriminated union. Only one payload is live at a time; the tag selects which one.
- **du_tag** (d1): A value-level or type-level label that uniquely identifies which variant of a discriminated union is active in a given value. The tag is the first-class evidence of variant membership.

## CONSUMERS (what needs this)
`discriminated_union`, `du_binary`, `du_exhaustiveness`, `du_inject`, `optics_type`, `prism_builder`, `prism_matcher`

---
*Projected from the `type systems for working programmers` KB (242 concepts / 186 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
