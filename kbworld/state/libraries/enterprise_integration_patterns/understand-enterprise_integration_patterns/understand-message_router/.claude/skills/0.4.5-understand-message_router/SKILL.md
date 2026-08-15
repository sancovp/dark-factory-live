---
name: 0.4.5-understand-message_router
description: [0.4.5] A component that inspects message content or metadata and forwards the message to one or more downstream chann
---

# understand-message_router

**CALL NUMBER:** `enterprise_integration_patterns.message_router : deep_message(6)`
**DEFINITION:** A component that inspects message content or metadata and forwards the message to one or more downstream channels.

Invoke this skill to understand `message_router` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_message`
- **dm_008** (d1): payload_extractor: A component that retrieves specific fields from the payload_structure for routing, correlation, or downstream transformation.
- **dm_001** (d2): payload_structure: The internal data shape of a document message, comprising typed fields and nested data elements that constitute the complete business data being transmitted.
- **dm_003** (d2): business_object_type: A typed classifier identifying the kind of business entity the document represents, such as purchase_order, invoice, or shipment_manifest.
- **dm_002** (d3): semantic_envelope: Metadata wrapper around the payload describing document provenance, intent classification, and temporal context without prescribing receiver action.
- **dm_005** (d4): content_identifier: A stable unique reference (document_id, correlation token) that identifies this specific document instance across systems and message stores.
- **dm_006** (d4): processing_hint: An optional non-directive annotation suggesting preferred handling, urgency, or routing preference without constituting a command.

### from `enterprise_integration_patterns`
- **content_based_router** (d1): A router that examines message payload fields to determine the destination channel, decoupling sender from destination knowledge.
- **dynamic_router** (d1): A router that consults a registry or lookup table at runtime to determine destinations, allowing routing rules to change without redeployment.
- **message_filter** (d1): A router that discards messages that do not meet a predicate condition, suppressing unwanted messages from downstream consumers.
- **recipient_list** (d1): A router that sends the same message to a list of recipients computed at runtime from the message content or context.
- **splitter** (d1): A router that breaks a composite message containing multiple items into individual messages, one per item.
- **normalizer** (d2): A transformer that reconciles multiple inbound message formats into a single canonical format before routing.
- **aggregator** (d2): A router that collects related messages over time and combines them into a single coherent output message.
- **bulk_message_consumer** (d2): A consumer that collects multiple messages over a batching window and processes them together for throughput optimization.
- **end_to_end_acknowledge** (d3): A correlation pattern where the final consumer sends an acknowledgment that propagates back through the routing chain to the original sender.
- **resequencer** (d3): A router that reorders a stream of messages into the correct sequence before passing them downstream.

## CONSUMERS (what needs this)
`command_message`, `delayer`, `message`, `throttler`

---
*Projected from the `enterprise integration patterns` KB (154 concepts / 176 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
