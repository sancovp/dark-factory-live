---
name: 0.3.1-understand-cp_purge_action
description: [0.3.1] The execution step that removes qualifying messages from the channel: permanent deletion, move to dead_letter_
---

# understand-cp_purge_action

**CALL NUMBER:** `deep_message_channel.cp_purge_action : deep_message(6), enterprise_integration_patterns(3)`
**DEFINITION:** The execution step that removes qualifying messages from the channel: permanent deletion, move to dead_letter_channel, or quarantine to invalid_message_channel.

Invoke this skill to understand `cp_purge_action` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_message`
- **dm_004** (d2): document_schema: A formal contract defining the expected payload_structure fields, their types, cardinality, and optionality for a given business_object_type.
- **dm_001** (d3): payload_structure: The internal data shape of a document message, comprising typed fields and nested data elements that constitute the complete business data being transmitted.
- **dm_002** (d4): semantic_envelope: Metadata wrapper around the payload describing document provenance, intent classification, and temporal context without prescribing receiver action.
- **dm_003** (d4): business_object_type: A typed classifier identifying the kind of business entity the document represents, such as purchase_order, invoice, or shipment_manifest.
- **dm_005** (d5): content_identifier: A stable unique reference (document_id, correlation token) that identifies this specific document instance across systems and message stores.
- **dm_006** (d5): processing_hint: An optional non-directive annotation suggesting preferred handling, urgency, or routing preference without constituting a command.

### from `deep_message_channel`
- **cp_poison_message** (d1): A message that has caused repeated processing failures or is structurally unprocessable and blocks channel progress if retained.
- **cp_purge_history** (d1): An audit log recording which messages were purged, when, under which policy, and the channel_state_snapshot at purge time for replay and tuning.
- **cp_stale_message** (d1): A message that has exceeded its relevance window or idle duration and no longer carries actionable data for downstream consumers.

### from `enterprise_integration_patterns`
- **dead_letter_channel** (d1): A channel where messages go after exhausting retries, signaling a delivery failure requiring intervention.
- **invalid_message_channel** (d1): A channel that captures malformed or unprocessable messages for manual inspection instead of blocking the main flow.
- **health_check_endpoint** (d2): A monitoring interface that exposes integration component status (channels healthy, queues depth, processing lag) for observability.

## CONSUMERS (what needs this)
`cp_purge_trigger`

---
*Projected from the `enterprise integration patterns` KB (154 concepts / 176 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
