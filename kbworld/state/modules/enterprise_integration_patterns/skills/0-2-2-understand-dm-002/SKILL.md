---
name: 0.2.2-understand-dm_002
description: "[0.2.2] semantic_envelope: Metadata wrapper around the payload describing document provenance, intent classification, "
---

# understand-dm_002

**CALL NUMBER:** `deep_message.dm_002`
**DEFINITION:** semantic_envelope: Metadata wrapper around the payload describing document provenance, intent classification, and temporal context without prescribing receiver action.

Invoke this skill to understand `dm_002` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_message`
- **dm_003** (d1): business_object_type: A typed classifier identifying the kind of business entity the document represents, such as purchase_order, invoice, or shipment_manifest.
- **dm_005** (d1): content_identifier: A stable unique reference (document_id, correlation token) that identifies this specific document instance across systems and message stores.
- **dm_006** (d1): processing_hint: An optional non-directive annotation suggesting preferred handling, urgency, or routing preference without constituting a command.

## CONSUMERS (what needs this)
`dm_001`, `dm_007`, `document_message`

---
*Projected from the `enterprise integration patterns` KB (154 concepts / 176 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
