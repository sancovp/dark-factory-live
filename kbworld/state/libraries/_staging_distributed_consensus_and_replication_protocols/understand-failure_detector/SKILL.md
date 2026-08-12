# understand-failure_detector

**CALL NUMBER:** `deep_consensus.failure_detector : distributed_consensus_and_replication_protocols(20), deep_raft(6)`
**DEFINITION:** Mechanism to distinguish crashed nodes from slow ones based on timeouts, heartbeats, or phi_accrual.

Invoke this skill to understand `failure_detector` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **agreement** (d7): The property that a set of distributed processes reach the same decision outcome on a given value. Uniform agreement requires all processes including those that later crash to decide identically; asymmetric agreement permits different decision classes for different process roles such as primary versus backup.

### from `deep_consensus`
- **failure_mode** (d1): Classification of ways components can fail: crash_stop, crash_recovery, omission, timing, response, arbitrary_byzantine.
- **byzantine_failure** (d2): Component exhibits arbitrary behavior including lies, omissions, or timing violations.
- **crash_failure** (d2): Component ceases operation entirely without warning or recovery attempt.
- **network_partition** (d2): Connectivity loss between node subgroups preventing inter-group communication.
- **shadow_operations** (d3): Redundant execution paths validated against primary to detect silent corruption.
- **replica_synchronization** (d4): Propagation of updates to ensure all replicas converge toward identical state.
- **availability** (d4): Probability system remains operational and accessible despite failures.
- **safety** (d4): Property requiring system never reaches inconsistent or invalid state.
- **gossip_dissemination** (d5): Probabilistic epidemic protocol spreading updates through pairwise exchanges.
- **liveness** (d5): Property requiring system to eventually respond or make progress under fair conditions.
- **quorum_read** (d5): Reading from sufficient replicas to guarantee seeing latest write.
- **quorum_write** (d5): Writing to sufficient replicas to guarantee subsequent readers see the value.
- **replication_factor** (d5): Count of replica copies maintained for durability and availability.
- **strong_quorum** (d5): Quorum where read and write quorums overlap (r + w > n).
- **view_change** (d10): Transition of consensus membership to new configuration after membership modification.

### from `deep_raft`
- **a005** (d5): Uniform agreement: all processes including those that later fail must decide on the same value, stricter than ordinary agreement which only binds correct processes.
- **a007** (d7): Quorum in agreement: a subset of processes sufficient to guarantee agreement can be reached, typically intersecting any valid quorum to ensure overlap.
- **a008** (d7): Threshold in agreement: the minimum number of correct processes required to guarantee safety and liveness under given failure assumptions.
- **a009** (d8): Asymmetric agreement: one class of processes (e.g., primary) must agree while another class (e.g., backups) may reach different decisions, used in primary-backup protocols.
- **a002** (d8): Validity in agreement: the decided value must have been proposed by some process in the system, guaranteeing agreements are grounded in actual proposals.
- **a004** (d9): Termination in agreement: every correct process eventually decides some value, ensuring the protocol makes progress and does not stall indefinitely.

### from `distributed_consensus_and_replication_protocols`
- **state_machine_replication** (d3): Technique where deterministic state machines are replicated across nodes via a common log.
- **recovery** (d3): Process of restoring a failed node or the system to a consistent state.
- **split_brain** (d3): Scenario where network partition causes multiple nodes to believe they are leader; resolved by quorum.
- **replicated_log** (d4): Ordered log of commands maintained across replicas; foundation of state machine replication.
- **roll_back** (d4): Reverting uncommitted changes to maintain consistency after transaction abort.
- **roll_forward** (d4): Reapplying committed log entries to reconstruct state after failure.
- **quorum** (d4): Subset of nodes sufficient for reads or writes; typically majority (n/2+1) for strong consistency.
- **anti_entropy** (d5): Repair of divergent replicas by comparing Merkle trees and exchanging differences.
- **read_repair** (d5): Background correction of stale replicas when read reveals outdated data.
- **linearizability** (d5): Strongest consistency model: every operation appears atomic and ordered in real time across all nodes.
- **semi_synchronous_replication** (d5): Write waits for quorum of replicas to acknowledge; balances latency and durability.
- **synchronous_replication** (d5): Write waits for all replicas to acknowledge before returning to client.
- **state_transfer** (d6): Sending full current state to a lagging replica for rapid catch-up.
- **eventual_consistency** (d6): Given no new updates, all replicas will eventually converge to the same value.
- **consensus** (d6): Agreement on a single value among a set of distributed processes; the core problem consensus protocols solve.
- **catch_up_recovery** (d7): Process of syncing a lagging or new replica with current leader state.
- **fault_tolerance** (d7): System's ability to continue operating correctly despite component failures.
- **reconfiguration** (d8): Process of changing cluster membership while maintaining consistency guarantees.
- **membership_change** (d9): Adding or removing nodes from the cluster without service interruption.
- **joint_consensus** (d10): Raft's two-phase configuration change using joint configuration of old and new members.

## CONSUMERS (what needs this)
`failure_detection_timeout`, `heartbeat`, `phi_accrual_detector`, `preemptive_recovery`

---
*Projected from the `distributed consensus and replication protocols` KB (196 concepts / 187 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*