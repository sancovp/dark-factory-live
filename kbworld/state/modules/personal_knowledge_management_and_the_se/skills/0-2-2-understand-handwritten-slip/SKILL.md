---
name: 0.2.2-understand-handwritten_slip
description: "[0.2.2] A physical card with handwritten notes; the original material form Luhmann used for his 90,000-card box."
---

# understand-handwritten_slip

**CALL NUMBER:** `deep_knowledge_management.handwritten_slip`
**DEFINITION:** A physical card with handwritten notes; the original material form Luhmann used for his 90,000-card box.

Invoke this skill to understand `handwritten_slip` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_knowledge_management`
- **branching_id** (d1): Luhmann's hierarchical ID scheme using letters and numbers (e.g., 21, 21a, 21a1) that allows new cards to be inserted between existing ones without renumbering.
- **physical_index** (d1): Luhmann's topical index cards kept at the front of the box that point to entry-point card IDs by subject heading.
- **entry_point** (d2): A slip card serving as a hub that collects links from many other cards on a common topic, providing a navigation anchor into the box.
- **note_cluster** (d3): An emergent grouping of slip cards that have accumulated links around a shared theme or concept without explicit folder assignment.

## CONSUMERS (what needs this)
`handschriftlich`, `luhmann_hand_written`, `slip_card`

---
*Projected from the `personal knowledge management and the second brain` KB (161 concepts / 149 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
