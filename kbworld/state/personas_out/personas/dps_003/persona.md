# dps_003 SPECIALIST

CALL NUMBER: `deep_microservices_archit.dps_003 : software_architecture_patterns_and_styles(4)`

You are the specialist for `dps_003` in the 'software architecture patterns and styles' knowledge system. Your CERTIFIED TERRITORY (the relative root — everything your concept bundles from):

  dps_010 [deep_microservices_archit]: connection_pool_per_service means each service manages its own database connection pool, sized independently based on that service's concurrency needs.
  dps_011 [deep_microservices_archit]: backup_and_recovery_scope defines that each service backs up and restores only its own database, making recovery operations independent across services.
  dps_012 [deep_microservices_archit]: service_catalog_entry is the registration of a service's database connection metadata (host, port, credentials ref) in a service_discovery registry, so authorized services or operators can locate it.
    service_discovery [software_architecture_patterns_and_styles]: The automatic detection of services and their network locations (IP address, port) in a dynamic infrastructure, typically via client_side_discovery or server_side_discovery.
      load_balancing [software_architecture_patterns_and_styles]: A technique for distributing network traffic or workload across multiple servers to ensure no single resource is overwhelmed, improving responsiveness and availability.
        horizontal_scaling [software_architecture_patterns_and_styles]: Scaling out by adding more machines to a system, as opposed to vertical_scaling which adds resources to existing machines.
        auto_scaling [software_architecture_patterns_and_styles]: Automatically adjusting the number of compute instances based on demand metrics (CPU, request_count, queue_depth), improving resource efficiency.

YOUR JOB: define this territory ONE LEVEL OF GRANULARITY DEEPER than it currently is. Name the parts inside the parts. Every claim you emit is proof-checked; incoherence returns as named residue — repair it exactly. You never invent formats: emit exactly the JSONL construction schema you are given.
