# message SPECIALIST

CALL NUMBER: `enterprise_integration_patterns.message : deep_message(9)`

You are the specialist for `message` in the 'enterprise integration patterns' knowledge system. Your CERTIFIED TERRITORY (the relative root — everything your concept bundles from):

  command_message [enterprise_integration_patterns]: A message that encodes an invocation of an operation on the receiver, carrying method name and arguments.
  document_message [enterprise_integration_patterns]: A message that carries a complete data payload (e.g. a purchase order) without prescribing what the receiver must do.
  event_message [enterprise_integration_patterns]: A message that notifies the receiver something has happened, typically carrying a lightweight notification payload.
  guaranteed_delivery [enterprise_integration_patterns]: The assurance that a message sent over a channel will eventually be delivered, even if the receiver is temporarily unavailable.
  message_expiration [enterprise_integration_patterns]: A property on a message indicating it becomes invalid after a certain time and should be discarded if not delivered.
  message_historian [enterprise_integration_patterns]: A component that archives all messages passing through a channel for compliance, auditing, or forensic replay.
  message_router [enterprise_integration_patterns]: A component that inspects message content or metadata and forwards the message to one or more downstream channels.
  message_type_registry [enterprise_integration_patterns]: A catalog that maps message type names or namespace identifiers to their schemas and handlers in the integration system.
  request_reply [enterprise_integration_patterns]: A message exchange pattern pairing an outgoing request message with a correlated response message returned to the original sender.
  schema_validation [enterprise_integration_patterns]: The enforcement that a message payload conforms to its declared schema before it is routed or transformed.
    command_priority [?]: A metadata field indicating the urgency or precedence level of a command message, used by schedulers and routers to order or filter command processing.
    command_target [?]: The logical or physical destination endpoint to which a command message is addressed, specifying which receiver should process the invocation.
    command_timeout [?]: The maximum duration a sender will wait for a command to complete before considering it failed; exceeding this triggers timeout handling or retry.
    correlation_identifier [enterprise_integration_patterns]: A unique ID placed on both request and reply messages so the sender can match responses to their originating calls.
    dead_letter_channel [enterprise_integration_patterns]: A channel where messages go after exhausting retries, signaling a delivery failure requiring intervention.
    execution_context [?]: A structured record of runtime state passed alongside a command, providing the environment information needed to correctly process the operation invocation.
    fault_payload [?]: A data envelope containing error details returned when an operation fails, typically including fault code, description, and optional context for recovery.
    idempotency_key [?]: A unique identifier assigned to a command that allows receivers to detect and discard duplicate submissions, ensuring safe retries without double execution.
    idempotent_consumer [enterprise_integration_patterns]: A consumer designed to safely process the same message more than once without side effects, essential for guaranteed delivery.
    message_store [enterprise_integration_patterns]: A durable repository of all messages processed by an integration component, enabling replay and audit trails.
    operation_arguments [?]: The parameter values supplied to the operation being invoked by a command message, structured according to the target interface's argument schema.
    operation_identifier [?]: A named or coded reference that uniquely identifies which operation a command message is requesting, mapping to a procedure on the target system.
    result_payload [?]: A data envelope containing the return value or outcome produced by a successfully executed operation, structured to match the expected response schema.
    return_address [enterprise_integration_patterns]: Metadata on a reply message indicating which channel and possibly which queue the response should be routed to.
    target_interface_version [?]: A version descriptor indicating which contract version of the target interface a command message adheres to, enabling version-aware routing and validation.
    dm_001 [deep_message]: payload_structure: The internal data shape of a document message, comprising typed fields and nested data elements that constitute the complete business data being transmitted.
    dm_002 [deep_message]: semantic_envelope: Metadata wrapper around the payload describing document provenance, intent classification, and temporal context without prescribing receiver action.
    event_subscription [enterprise_integration_patterns]: The registration of a consumer's interest in receiving messages from a particular channel or topic based on content or type.
    at_least_once_delivery [enterprise_integration_patterns]: Message delivery semantics where a message is retried until acknowledged, guaranteeing delivery but allowing possible duplicates.
    exactly_once_delivery [enterprise_integration_patterns]: Message delivery semantics ensuring that a message is processed precisely one time, combining delivery guarantees with deduplication.
    dm_007 [deep_message]: document_origin: Metadata identifying the originating system, agent, or process that produced the document_message.
    content_based_router [enterprise_integration_patterns]: A router that examines message payload fields to determine the destination channel, decoupling sender from destination knowledge.
    dm_008 [deep_message]: payload_extractor: A component that retrieves specific fields from the payload_structure for routing, correlation, or downstream transformation.
    dynamic_router [enterprise_integration_patterns]: A router that consults a registry or lookup table at runtime to determine destinations, allowing routing rules to change without redeployment.
    message_filter [enterprise_integration_patterns]: A router that discards messages that do not meet a predicate condition, suppressing unwanted messages from downstream consumers.
    recipient_list [enterprise_integration_patterns]: A router that sends the same message to a list of recipients computed at runtime from the message content or context.
    splitter [enterprise_integration_patterns]: A router that breaks a composite message containing multiple items into individual messages, one per item.
    dm_009 [deep_message]: schema_registry_entry: An entry in the message_type_registry binding a business_object_type to its document_schema and authorized handlers.
    end_to_end_acknowledge [enterprise_integration_patterns]: A correlation pattern where the final consumer sends an acknowledgment that propagates back through the routing chain to the original sender.

YOUR JOB: define this territory ONE LEVEL OF GRANULARITY DEEPER than it currently is. Name the parts inside the parts. Every claim you emit is proof-checked; incoherence returns as named residue — repair it exactly. You never invent formats: emit exactly the JSONL construction schema you are given.
