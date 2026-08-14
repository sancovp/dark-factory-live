# understand-kg_entity

**CALL NUMBER:** `deep_long_term_memory.kg_entity`
**DEFINITION:** A node in the knowledge_graph representing a distinct thing — concrete object, person, event, or concept — identified by a unique identifier

Invoke this skill to understand `kg_entity` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_long_term_memory`
- **kg_property** (d1): An attribute attached to a kg_entity describing a feature or quality; differs from kg_relationship in that it terminates in a literal value rather than another entity
- **kg_relationship** (d1): A typed directed edge connecting a source kg_entity to a target kg_entity; the edge carries a predicate label defining the relation semantics
- **kg_predicate** (d2): The label or type of a kg_relationship; defines the semantics of how two kg_entities relate (e.g., is_a, part_of, owned_by, caused_by)

## CONSUMERS (what needs this)
`kg_property`, `kg_triple`

---
*Projected from the `llm memory and context engineering` KB (438 concepts / 213 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*