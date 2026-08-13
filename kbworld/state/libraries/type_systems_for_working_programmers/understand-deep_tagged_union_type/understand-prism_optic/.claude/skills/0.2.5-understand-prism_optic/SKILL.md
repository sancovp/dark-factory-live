---
name: 0.2.5-understand-prism_optic
description: [0.2.5] An optic pairing a matcher with a builder over a sum type's du_variant, enabling partial projection into one d
---

# understand-prism_optic

**CALL NUMBER:** `deep_tagged_union_type.prism_optic`
**DEFINITION:** An optic pairing a matcher with a builder over a sum type's du_variant, enabling partial projection into one du_tag's du_payload with fallback to the original sum.

Invoke this skill to understand `prism_optic` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_tagged_union_type`
- **optic_variance** (d1): Classification of an optic by its directional capability: getter-only (covariant, read-only), setter-only (contravariant, write-only), or full optic (both directions, lenses are the canonical full case).
- **prism_builder** (d1): A constructor taking a du_payload and injecting it as the sole du_variant under a specific du_tag, rebuilding the sum type from the selected summand.
- **prism_matcher** (d1): A partial function over a sum type that succeeds only when the active du_tag matches the target, yielding the contained du_payload; otherwise the sum is preserved.
- **lens_optic** (d2): An optic pairing a getter with a setter over a product type's field, enabling focused access to one du_payload while preserving the rest of the product structure.
- **du_tag** (d2): A value-level or type-level label that uniquely identifies which variant of a discriminated union is active in a given value. The tag is the first-class evidence of variant membership.
- **du_variant** (d2): A named constituent of a discriminated union, pairing a du_tag with a du_payload type. Each variant represents one summand in the sum type.
- **lens_getter** (d3): A pure projection from a product type to a specific du_payload at a named field, extracting only the target substructure without mutation.
- **lens_setter** (d3): A mutation function taking a product type and a new du_payload value, returning a new product with only the target field replaced, leaving all other du_payload fields unchanged.
- **optic_law_get_set** (d3): Law: applying lens_setter to the result of lens_getter on any product yields back the original du_payload value — get never lies about what set just wrote.
- **optic_law_set_get** (d3): Law: applying lens_getter to the result of lens_setter on a product yields back the du_payload value that was set — set reflects exactly what get will retrieve.
- **optic_law_set_set** (d3): Law: composing two lens_setter calls yields the same product as applying only the second one — idempotent in the face of duplicate mutation, last du_payload wins.
- **optic_law_unity** (d3): Law: the composition of a lens_setter with a lens_getter in reverse order yields a total transformation equivalent to the identity on du_payload — structural integrity preserved under round-trip.
- **du_payload** (d3): The data value carried by a specific variant of a discriminated union. Only one payload is live at a time; the tag selects which one.

## CONSUMERS (what needs this)
`optic_compose`, `optics_type`

---
*Projected from the `type systems for working programmers` KB (242 concepts / 186 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
