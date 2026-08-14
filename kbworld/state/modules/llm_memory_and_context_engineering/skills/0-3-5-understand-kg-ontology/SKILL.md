---
name: 0.3.5-understand-kg_ontology
description: "[0.3.5] The schema layer of a knowledge_graph defining allowed kg_entity types (classes), allowed kg_predicate labels,"
---

# understand-kg_ontology

**CALL NUMBER:** `deep_long_term_memory.kg_ontology`
**DEFINITION:** The schema layer of a knowledge_graph defining allowed kg_entity types (classes), allowed kg_predicate labels, and domain/range constraints on kg_relationships

Invoke this skill to understand `kg_ontology` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **is_a** (d2): A taxonomic relationship linking a kg_instance to its kg_class, establishing membership and enabling inheritance of class-defined properties and constraints.

### from `deep_long_term_memory`
- **kg_class** (d1): A kg_entity type within the kg_ontology; groups instances that share structural or semantic properties
- **kg_predicate** (d1): The label or type of a kg_relationship; defines the semantics of how two kg_entities relate (e.g., is_a, part_of, owned_by, caused_by)
- **kg_schema** (d1): The structural blueprint specifying which kg_predicate labels are permitted between which kg_entity types; enforced by kg_ontology constraints

---
*Projected from the `llm memory and context engineering` KB (438 concepts / 213 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
