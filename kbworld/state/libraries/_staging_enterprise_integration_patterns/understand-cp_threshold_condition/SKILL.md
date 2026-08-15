# understand-cp_threshold_condition

**CALL NUMBER:** `deep_message_channel.cp_threshold_condition : deep_message(6), enterprise_integration_patterns(3)`
**DEFINITION:** A predicate over channel_state_snapshot values that evaluates to true when purge_trigger should fire, such as depth_overflow or stale_age_exceeded.

Invoke this skill to understand `cp_threshold_condition` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_message`
- **dm_004** (d4): document_schema: A formal contract defining the expected payload_structure fields, their types, cardinality, and optionality for a given business_object_type.
- **dm_001** (d5): payload_structure: The internal data shape of a document message, comprising typed fields and nested data elements that constitute the complete business data being transmitted.
- **dm_002** (d6): semantic_envelope: Metadata wrapper around the payload describing document provenance, intent classification, and temporal context without prescribing receiver action.
- **dm_003** (d6): business_object_type: A typed classifier identifying the kind of business entity the document represents, such as purchase_order, invoice, or shipment_manifest.
- **dm_005** (d7): content_identifier: A stable unique reference (document_id, correlation token) that identifies this specific document instance across systems and message stores.
- **dm_006** (d7): processing_hint: An optional non-directive annotation suggesting preferred handling, urgency, or routing preference without constituting a command.

### from `deep_message_channel`
- **cp_purge_trigger** (d1): A condition that initiates a channel purge cycle; may be time-based, count-based, or event-based such as threshold_exceeded.
- **cp_purge_action** (d2): The execution step that removes qualifying messages from the channel: permanent deletion, move to dead_letter_channel, or quarantine to invalid_message_channel.
- **cp_poison_message** (d3): A message that has caused repeated processing failures or is structurally unprocessable and blocks channel progress if retained.
- **cp_purge_history** (d3): An audit log recording which messages were purged, when, under which policy, and the channel_state_snapshot at purge time for replay and tuning.
- **cp_stale_message** (d3): A message that has exceeded its relevance window or idle duration and no longer carries actionable data for downstream consumers.

### from `enterprise_integration_patterns`
- **dead_letter_channel** (d3): A channel where messages go after exhausting retries, signaling a delivery failure requiring intervention.
- **invalid_message_channel** (d3): A channel that captures malformed or unprocessable messages for manual inspection instead of blocking the main flow.
- **health_check_endpoint** (d4): A monitoring interface that exposes integration component status (channels healthy, queues depth, processing lag) for observability.

## CONSUMERS (what needs this)
`cp_channel_state_snapshot`, `cp_purge_scheduler`

---
*Projected from the `enterprise integration patterns` KB (154 concepts / 176 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*