---
name: 0.4.3-understand-discriminated_union
description: "[0.4.3] Tagged union enabling compiler-verified exhaustive pattern matching over variants."
---

# understand-discriminated_union

**CALL NUMBER:** `type_systems_for_working_programmers.discriminated_union : deep_tagged_union_type(7)`
**DEFINITION:** Tagged union enabling compiler-verified exhaustive pattern matching over variants.

Invoke this skill to understand `discriminated_union` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **primitive_union** (d3): An untagged union of types representing a value that could be one of several member types, but without a discriminator tag or label to identify which variant is active at runtime. Membership cannot be compiler-verified and exhaustive pattern matching is not enforced.

### from `deep_tagged_union_type`
- **du_exhaustiveness** (d1): The static guarantee that a du_match covers every du_variant of the discriminated union. The type system rejects non-exhaustive matches, ensuring no variant is silently ignored.
- **du_inject** (d1): The introduction form for a discriminated union: given a variant label and a payload of the matching type, produce a value of the union type. Also called 'variant' or 'Left'/'Right' in binary cases.
- **du_match** (d1): The elimination form: a function that, given a discriminated union value, dispatches on its du_tag to apply the appropriate handler to the du_payload, yielding a uniform result type.
- **du_variant** (d1): A named constituent of a discriminated union, pairing a du_tag with a du_payload type. Each variant represents one summand in the sum type.
- **du_primitive** (d2): An untagged union of types without a du_tag. The discriminated union adds a tag to this primitive structure to make variant membership verifiable.
- **du_payload** (d2): The data value carried by a specific variant of a discriminated union. Only one payload is live at a time; the tag selects which one.
- **du_tag** (d2): A value-level or type-level label that uniquely identifies which variant of a discriminated union is active in a given value. The tag is the first-class evidence of variant membership.

### from `type_systems_for_working_programmers`
- **algebraic_data_type** (d1): Type formed by sum (union) and product (record) of other types.
- **type_safe_union** (d1): Tagged union with exhaustiveness guarantee preventing access without matching on tag.

## CONSUMERS (what needs this)
`tagged_union_type`

---
*Projected from the `type systems for working programmers` KB (242 concepts / 186 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
