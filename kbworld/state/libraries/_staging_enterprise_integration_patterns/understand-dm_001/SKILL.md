# understand-dm_001

**CALL NUMBER:** `deep_message.dm_001`
**DEFINITION:** payload_structure: The internal data shape of a document message, comprising typed fields and nested data elements that constitute the complete business data being transmitted.

Invoke this skill to understand `dm_001` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_message`
- **dm_002** (d1): semantic_envelope: Metadata wrapper around the payload describing document provenance, intent classification, and temporal context without prescribing receiver action.
- **dm_003** (d1): business_object_type: A typed classifier identifying the kind of business entity the document represents, such as purchase_order, invoice, or shipment_manifest.
- **dm_005** (d2): content_identifier: A stable unique reference (document_id, correlation token) that identifies this specific document instance across systems and message stores.
- **dm_006** (d2): processing_hint: An optional non-directive annotation suggesting preferred handling, urgency, or routing preference without constituting a command.

## CONSUMERS (what needs this)
`content_based_router`, `dm_004`, `document_message`, `normalizer`

---
*Projected from the `enterprise integration patterns` KB (154 concepts / 176 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*