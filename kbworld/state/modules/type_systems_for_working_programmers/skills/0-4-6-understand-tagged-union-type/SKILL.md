---
name: 0.4.6-understand-tagged_union_type
description: "[0.4.6] Discriminated union with explicit tag field enabling exhaustive pattern matching."
---

# understand-tagged_union_type

**CALL NUMBER:** `type_systems_for_working_programmers.tagged_union_type : deep_tagged_union_type(23)`
**DEFINITION:** Discriminated union with explicit tag field enabling exhaustive pattern matching.

Invoke this skill to understand `tagged_union_type` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **primitive_union** (d4): An untagged union of types representing a value that could be one of several member types, but without a discriminator tag or label to identify which variant is active at runtime. Membership cannot be compiler-verified and exhaustive pattern matching is not enforced.

### from `deep_tagged_union_type`
- **du_exhaustiveness** (d2): The static guarantee that a du_match covers every du_variant of the discriminated union. The type system rejects non-exhaustive matches, ensuring no variant is silently ignored.
- **du_inject** (d2): The introduction form for a discriminated union: given a variant label and a payload of the matching type, produce a value of the union type. Also called 'variant' or 'Left'/'Right' in binary cases.
- **du_match** (d2): The elimination form: a function that, given a discriminated union value, dispatches on its du_tag to apply the appropriate handler to the du_payload, yielding a uniform result type.
- **du_variant** (d2): A named constituent of a discriminated union, pairing a du_tag with a du_payload type. Each variant represents one summand in the sum type.
- **iso_optic** (d2): A bidirectional optic between two types that are isomorphic, providing both a forward view and a reverse constructor with no information loss.
- **lens_optic** (d2): An optic pairing a getter with a setter over a product type's field, enabling focused access to one du_payload while preserving the rest of the product structure.
- **optic_compose** (d2): Composition rule: chaining optics so the du_payload of one becomes the structure operated on by the next, forming a pipeline that satisfies the optic laws transitively.
- **optic_law_get_set** (d2): Law: applying lens_setter to the result of lens_getter on any product yields back the original du_payload value — get never lies about what set just wrote.
- **optic_law_set_get** (d2): Law: applying lens_getter to the result of lens_setter on a product yields back the du_payload value that was set — set reflects exactly what get will retrieve.
- **optic_law_set_set** (d2): Law: composing two lens_setter calls yields the same product as applying only the second one — idempotent in the face of duplicate mutation, last du_payload wins.
- **optic_law_unity** (d2): Law: the composition of a lens_setter with a lens_getter in reverse order yields a total transformation equivalent to the identity on du_payload — structural integrity preserved under round-trip.
- **optic_variance** (d2): Classification of an optic by its directional capability: getter-only (covariant, read-only), setter-only (contravariant, write-only), or full optic (both directions, lenses are the canonical full case).
- **prism_optic** (d2): An optic pairing a matcher with a builder over a sum type's du_variant, enabling partial projection into one du_tag's du_payload with fallback to the original sum.
- **traversal_optic** (d2): An optic generalizing lens and prism to target zero or more locations simultaneously, enabling fold and map operations over collections of du_payload within a structure.
- **du_primitive** (d3): An untagged union of types without a du_tag. The discriminated union adds a tag to this primitive structure to make variant membership verifiable.
- **du_payload** (d3): The data value carried by a specific variant of a discriminated union. Only one payload is live at a time; the tag selects which one.
- **du_tag** (d3): A value-level or type-level label that uniquely identifies which variant of a discriminated union is active in a given value. The tag is the first-class evidence of variant membership.
- **lens_getter** (d3): A pure projection from a product type to a specific du_payload at a named field, extracting only the target substructure without mutation.
- **lens_setter** (d3): A mutation function taking a product type and a new du_payload value, returning a new product with only the target field replaced, leaving all other du_payload fields unchanged.
- **prism_builder** (d3): A constructor taking a du_payload and injecting it as the sole du_variant under a specific du_tag, rebuilding the sum type from the selected summand.
- **prism_matcher** (d3): A partial function over a sum type that succeeds only when the active du_tag matches the target, yielding the contained du_payload; otherwise the sum is preserved.
- **traversal_fold** (d3): Operation over a traversal_optic that reduces all targeted du_payload within a structure to a single aggregate value, consuming the structure without producing a new one.
- **traversal_map** (d3): Operation over a traversal_optic that applies a function to each du_payload in the targeted locations, producing a new structure with all positions updated.

### from `type_systems_for_working_programmers`
- **algebraic_data_type** (d1): Type formed by sum (union) and product (record) of other types.
- **discriminated_union** (d1): Tagged union enabling compiler-verified exhaustive pattern matching over variants.
- **optics_type** (d1): Abstracting getters/setters across product and sum types (lens, prism, traversal).
- **type_safe_union** (d1): Tagged union with exhaustiveness guarantee preventing access without matching on tag.

---
*Projected from the `type systems for working programmers` KB (242 concepts / 186 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
