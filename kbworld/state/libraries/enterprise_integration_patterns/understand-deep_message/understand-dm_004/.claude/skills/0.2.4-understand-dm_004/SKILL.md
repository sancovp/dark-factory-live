---
name: 0.2.4-understand-dm_004
description: [0.2.4] document_schema: A formal contract defining the expected payload_structure fields, their types, cardinality, a
---

# understand-dm_004

**CALL NUMBER:** `deep_message.dm_004`
**DEFINITION:** document_schema: A formal contract defining the expected payload_structure fields, their types, cardinality, and optionality for a given business_object_type.

Invoke this skill to understand `dm_004` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_message`
- **dm_001** (d1): payload_structure: The internal data shape of a document message, comprising typed fields and nested data elements that constitute the complete business data being transmitted.
- **dm_002** (d2): semantic_envelope: Metadata wrapper around the payload describing document provenance, intent classification, and temporal context without prescribing receiver action.
- **dm_003** (d2): business_object_type: A typed classifier identifying the kind of business entity the document represents, such as purchase_order, invoice, or shipment_manifest.
- **dm_005** (d3): content_identifier: A stable unique reference (document_id, correlation token) that identifies this specific document instance across systems and message stores.
- **dm_006** (d3): processing_hint: An optional non-directive annotation suggesting preferred handling, urgency, or routing preference without constituting a command.

## CONSUMERS (what needs this)
`dead_letter_channel`, `schema_validation`

---
*Projected from the `enterprise integration patterns` KB (154 concepts / 176 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
