---
name: 0.4.1-understand-optics_type
description: [0.4.1] Abstracting getters/setters across product and sum types (lens, prism, traversal).
---

# understand-optics_type

**CALL NUMBER:** `type_systems_for_working_programmers.optics_type : deep_tagged_union_type(19)`
**DEFINITION:** Abstracting getters/setters across product and sum types (lens, prism, traversal).

Invoke this skill to understand `optics_type` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_tagged_union_type`
- **du_variant** (d1): A named constituent of a discriminated union, pairing a du_tag with a du_payload type. Each variant represents one summand in the sum type.
- **iso_optic** (d1): A bidirectional optic between two types that are isomorphic, providing both a forward view and a reverse constructor with no information loss.
- **lens_optic** (d1): An optic pairing a getter with a setter over a product type's field, enabling focused access to one du_payload while preserving the rest of the product structure.
- **optic_compose** (d1): Composition rule: chaining optics so the du_payload of one becomes the structure operated on by the next, forming a pipeline that satisfies the optic laws transitively.
- **optic_law_get_set** (d1): Law: applying lens_setter to the result of lens_getter on any product yields back the original du_payload value — get never lies about what set just wrote.
- **optic_law_set_get** (d1): Law: applying lens_getter to the result of lens_setter on a product yields back the du_payload value that was set — set reflects exactly what get will retrieve.
- **optic_law_set_set** (d1): Law: composing two lens_setter calls yields the same product as applying only the second one — idempotent in the face of duplicate mutation, last du_payload wins.
- **optic_law_unity** (d1): Law: the composition of a lens_setter with a lens_getter in reverse order yields a total transformation equivalent to the identity on du_payload — structural integrity preserved under round-trip.
- **optic_variance** (d1): Classification of an optic by its directional capability: getter-only (covariant, read-only), setter-only (contravariant, write-only), or full optic (both directions, lenses are the canonical full case).
- **prism_optic** (d1): An optic pairing a matcher with a builder over a sum type's du_variant, enabling partial projection into one du_tag's du_payload with fallback to the original sum.
- **traversal_optic** (d1): An optic generalizing lens and prism to target zero or more locations simultaneously, enabling fold and map operations over collections of du_payload within a structure.
- **du_payload** (d2): The data value carried by a specific variant of a discriminated union. Only one payload is live at a time; the tag selects which one.
- **du_tag** (d2): A value-level or type-level label that uniquely identifies which variant of a discriminated union is active in a given value. The tag is the first-class evidence of variant membership.
- **lens_getter** (d2): A pure projection from a product type to a specific du_payload at a named field, extracting only the target substructure without mutation.
- **lens_setter** (d2): A mutation function taking a product type and a new du_payload value, returning a new product with only the target field replaced, leaving all other du_payload fields unchanged.
- **prism_builder** (d2): A constructor taking a du_payload and injecting it as the sole du_variant under a specific du_tag, rebuilding the sum type from the selected summand.
- **prism_matcher** (d2): A partial function over a sum type that succeeds only when the active du_tag matches the target, yielding the contained du_payload; otherwise the sum is preserved.
- **traversal_fold** (d2): Operation over a traversal_optic that reduces all targeted du_payload within a structure to a single aggregate value, consuming the structure without producing a new one.
- **traversal_map** (d2): Operation over a traversal_optic that applies a function to each du_payload in the targeted locations, producing a new structure with all positions updated.

## CONSUMERS (what needs this)
`tagged_union_type`

---
*Projected from the `type systems for working programmers` KB (242 concepts / 186 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
