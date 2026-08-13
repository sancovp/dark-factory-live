---
name: 0.2.2-understand-lens_optic
description: "[0.2.2] An optic pairing a getter with a setter over a product type's field, enabling focused access to one du_payload"
---

# understand-lens_optic

**CALL NUMBER:** `deep_tagged_union_type.lens_optic`
**DEFINITION:** An optic pairing a getter with a setter over a product type's field, enabling focused access to one du_payload while preserving the rest of the product structure.

Invoke this skill to understand `lens_optic` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_tagged_union_type`
- **lens_getter** (d1): A pure projection from a product type to a specific du_payload at a named field, extracting only the target substructure without mutation.
- **lens_setter** (d1): A mutation function taking a product type and a new du_payload value, returning a new product with only the target field replaced, leaving all other du_payload fields unchanged.
- **optic_law_get_set** (d1): Law: applying lens_setter to the result of lens_getter on any product yields back the original du_payload value — get never lies about what set just wrote.
- **optic_law_set_get** (d1): Law: applying lens_getter to the result of lens_setter on a product yields back the du_payload value that was set — set reflects exactly what get will retrieve.
- **optic_law_set_set** (d1): Law: composing two lens_setter calls yields the same product as applying only the second one — idempotent in the face of duplicate mutation, last du_payload wins.
- **optic_law_unity** (d1): Law: the composition of a lens_setter with a lens_getter in reverse order yields a total transformation equivalent to the identity on du_payload — structural integrity preserved under round-trip.
- **du_payload** (d2): The data value carried by a specific variant of a discriminated union. Only one payload is live at a time; the tag selects which one.

## CONSUMERS (what needs this)
`optic_compose`, `optic_variance`, `optics_type`

---
*Projected from the `type systems for working programmers` KB (242 concepts / 186 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
