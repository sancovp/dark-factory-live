---
name: 0.2.4-understand-failure_mode
description: "[0.2.4] Classification of ways components can fail: crash_stop, crash_recovery, omission, timing, response, arbitrary_"
---

# understand-failure_mode

**CALL NUMBER:** `deep_consensus.failure_mode : distributed_consensus_and_replication_protocols(20), deep_raft(6)`
**DEFINITION:** Classification of ways components can fail: crash_stop, crash_recovery, omission, timing, response, arbitrary_byzantine.

Invoke this skill to understand `failure_mode` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **agreement** (d6): The property that a set of distributed processes reach the same decision outcome on a given value. Uniform agreement requires all processes including those that later crash to decide identically; asymmetric agreement permits different decision classes for different process roles such as primary versus backup.

### from `deep_consensus`
- **byzantine_failure** (d1): Component exhibits arbitrary behavior including lies, omissions, or timing violations.
- **crash_failure** (d1): Component ceases operation entirely without warning or recovery attempt.
- **network_partition** (d1): Connectivity loss between node subgroups preventing inter-group communication.
- **shadow_operations** (d2): Redundant execution paths validated against primary to detect silent corruption.
- **replica_synchronization** (d3): Propagation of updates to ensure all replicas converge toward identical state.
- **availability** (d3): Probability system remains operational and accessible despite failures.
- **safety** (d3): Property requiring system never reaches inconsistent or invalid state.
- **gossip_dissemination** (d4): Probabilistic epidemic protocol spreading updates through pairwise exchanges.
- **liveness** (d4): Property requiring system to eventually respond or make progress under fair conditions.
- **quorum_read** (d4): Reading from sufficient replicas to guarantee seeing latest write.
- **quorum_write** (d4): Writing to sufficient replicas to guarantee subsequent readers see the value.
- **replication_factor** (d4): Count of replica copies maintained for durability and availability.
- **strong_quorum** (d4): Quorum where read and write quorums overlap (r + w > n).
- **view_change** (d9): Transition of consensus membership to new configuration after membership modification.

### from `deep_raft`
- **a005** (d4): Uniform agreement: all processes including those that later fail must decide on the same value, stricter than ordinary agreement which only binds correct processes.
- **a007** (d6): Quorum in agreement: a subset of processes sufficient to guarantee agreement can be reached, typically intersecting any valid quorum to ensure overlap.
- **a008** (d6): Threshold in agreement: the minimum number of correct processes required to guarantee safety and liveness under given failure assumptions.
- **a009** (d7): Asymmetric agreement: one class of processes (e.g., primary) must agree while another class (e.g., backups) may reach different decisions, used in primary-backup protocols.
- **a002** (d7): Validity in agreement: the decided value must have been proposed by some process in the system, guaranteeing agreements are grounded in actual proposals.
- **a004** (d8): Termination in agreement: every correct process eventually decides some value, ensuring the protocol makes progress and does not stall indefinitely.

### from `distributed_consensus_and_replication_protocols`
- **state_machine_replication** (d2): Technique where deterministic state machines are replicated across nodes via a common log.
- **recovery** (d2): Process of restoring a failed node or the system to a consistent state.
- **split_brain** (d2): Scenario where network partition causes multiple nodes to believe they are leader; resolved by quorum.
- **replicated_log** (d3): Ordered log of commands maintained across replicas; foundation of state machine replication.
- **roll_back** (d3): Reverting uncommitted changes to maintain consistency after transaction abort.
- **roll_forward** (d3): Reapplying committed log entries to reconstruct state after failure.
- **quorum** (d3): Subset of nodes sufficient for reads or writes; typically majority (n/2+1) for strong consistency.
- **anti_entropy** (d4): Repair of divergent replicas by comparing Merkle trees and exchanging differences.
- **read_repair** (d4): Background correction of stale replicas when read reveals outdated data.
- **linearizability** (d4): Strongest consistency model: every operation appears atomic and ordered in real time across all nodes.
- **semi_synchronous_replication** (d4): Write waits for quorum of replicas to acknowledge; balances latency and durability.
- **synchronous_replication** (d4): Write waits for all replicas to acknowledge before returning to client.
- **state_transfer** (d5): Sending full current state to a lagging replica for rapid catch-up.
- **eventual_consistency** (d5): Given no new updates, all replicas will eventually converge to the same value.
- **consensus** (d5): Agreement on a single value among a set of distributed processes; the core problem consensus protocols solve.
- **catch_up_recovery** (d6): Process of syncing a lagging or new replica with current leader state.
- **fault_tolerance** (d6): System's ability to continue operating correctly despite component failures.
- **reconfiguration** (d7): Process of changing cluster membership while maintaining consistency guarantees.
- **membership_change** (d8): Adding or removing nodes from the cluster without service interruption.
- **joint_consensus** (d9): Raft's two-phase configuration change using joint configuration of old and new members.

## CONSUMERS (what needs this)
`failure_detector`

---
*Projected from the `distributed consensus and replication protocols` KB (196 concepts / 187 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
