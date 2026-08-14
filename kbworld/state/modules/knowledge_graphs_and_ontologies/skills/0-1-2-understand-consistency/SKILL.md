---
name: 0.1.2-understand-consistency
description: "[0.1.2] A reasoning task verifying that an ontology has no contradictory axioms that would eliminate all possible mode"
---

# understand-consistency

**CALL NUMBER:** `knowledge_graphs_and_ontologies.consistency`
**DEFINITION:** A reasoning task verifying that an ontology has no contradictory axioms that would eliminate all possible models.

Invoke this skill to understand `consistency` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `knowledge_graphs_and_ontologies`
- **satisfiability** (d1): A reasoning task determining whether an ontology or class description can have any valid model satisfying all axioms.

## CONSUMERS (what needs this)
`coherence`

---
*Projected from the `knowledge graphs and ontologies` KB (177 concepts / 20 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
