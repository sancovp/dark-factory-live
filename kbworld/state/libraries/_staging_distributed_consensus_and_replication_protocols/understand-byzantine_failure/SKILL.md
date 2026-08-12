# understand-byzantine_failure

**CALL NUMBER:** `deep_consensus.byzantine_failure : distributed_consensus_and_replication_protocols(12), deep_raft(6)`
**DEFINITION:** Component exhibits arbitrary behavior including lies, omissions, or timing violations.

Invoke this skill to understand `byzantine_failure` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **agreement** (d5): The property that a set of distributed processes reach the same decision outcome on a given value. Uniform agreement requires all processes including those that later crash to decide identically; asymmetric agreement permits different decision classes for different process roles such as primary versus backup.

### from `deep_consensus`
- **shadow_operations** (d1): Redundant execution paths validated against primary to detect silent corruption.
- **replica_synchronization** (d2): Propagation of updates to ensure all replicas converge toward identical state.
- **gossip_dissemination** (d3): Probabilistic epidemic protocol spreading updates through pairwise exchanges.
- **view_change** (d8): Transition of consensus membership to new configuration after membership modification.

### from `deep_raft`
- **a005** (d3): Uniform agreement: all processes including those that later fail must decide on the same value, stricter than ordinary agreement which only binds correct processes.
- **a007** (d5): Quorum in agreement: a subset of processes sufficient to guarantee agreement can be reached, typically intersecting any valid quorum to ensure overlap.
- **a008** (d5): Threshold in agreement: the minimum number of correct processes required to guarantee safety and liveness under given failure assumptions.
- **a009** (d6): Asymmetric agreement: one class of processes (e.g., primary) must agree while another class (e.g., backups) may reach different decisions, used in primary-backup protocols.
- **a002** (d6): Validity in agreement: the decided value must have been proposed by some process in the system, guaranteeing agreements are grounded in actual proposals.
- **a004** (d7): Termination in agreement: every correct process eventually decides some value, ensuring the protocol makes progress and does not stall indefinitely.

### from `distributed_consensus_and_replication_protocols`
- **state_machine_replication** (d1): Technique where deterministic state machines are replicated across nodes via a common log.
- **replicated_log** (d2): Ordered log of commands maintained across replicas; foundation of state machine replication.
- **anti_entropy** (d3): Repair of divergent replicas by comparing Merkle trees and exchanging differences.
- **read_repair** (d3): Background correction of stale replicas when read reveals outdated data.
- **state_transfer** (d4): Sending full current state to a lagging replica for rapid catch-up.
- **eventual_consistency** (d4): Given no new updates, all replicas will eventually converge to the same value.
- **consensus** (d4): Agreement on a single value among a set of distributed processes; the core problem consensus protocols solve.
- **catch_up_recovery** (d5): Process of syncing a lagging or new replica with current leader state.
- **fault_tolerance** (d5): System's ability to continue operating correctly despite component failures.
- **reconfiguration** (d6): Process of changing cluster membership while maintaining consistency guarantees.
- **membership_change** (d7): Adding or removing nodes from the cluster without service interruption.
- **joint_consensus** (d8): Raft's two-phase configuration change using joint configuration of old and new members.

## CONSUMERS (what needs this)
`byzantine_fault`, `failure_mode`

---
*Projected from the `distributed consensus and replication protocols` KB (196 concepts / 187 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*