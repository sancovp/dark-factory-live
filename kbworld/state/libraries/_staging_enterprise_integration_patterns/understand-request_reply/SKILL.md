# understand-request_reply

**CALL NUMBER:** `enterprise_integration_patterns.request_reply`
**DEFINITION:** A message exchange pattern pairing an outgoing request message with a correlated response message returned to the original sender.

Invoke this skill to understand `request_reply` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **fault_payload** (d1): A data envelope containing error details returned when an operation fails, typically including fault code, description, and optional context for recovery.
- **result_payload** (d1): A data envelope containing the return value or outcome produced by a successfully executed operation, structured to match the expected response schema.

### from `enterprise_integration_patterns`
- **correlation_identifier** (d1): A unique ID placed on both request and reply messages so the sender can match responses to their originating calls.
- **end_to_end_acknowledge** (d1): A correlation pattern where the final consumer sends an acknowledgment that propagates back through the routing chain to the original sender.
- **return_address** (d1): Metadata on a reply message indicating which channel and possibly which queue the response should be routed to.

## CONSUMERS (what needs this)
`command_message`, `message`

---
*Projected from the `enterprise integration patterns` KB (154 concepts / 176 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*