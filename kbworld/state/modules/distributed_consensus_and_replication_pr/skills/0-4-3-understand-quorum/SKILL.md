---
name: 0.4.3-understand-quorum
description: "[0.4.3] Subset of nodes sufficient for reads or writes; typically majority (n/2+1) for strong consistency."
---

# understand-quorum

**CALL NUMBER:** `distributed_consensus_and_replication_protocols.quorum : deep_raft(6), deep_consensus(4)`
**DEFINITION:** Subset of nodes sufficient for reads or writes; typically majority (n/2+1) for strong consistency.

Invoke this skill to understand `quorum` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **agreement** (d3): The property that a set of distributed processes reach the same decision outcome on a given value. Uniform agreement requires all processes including those that later crash to decide identically; asymmetric agreement permits different decision classes for different process roles such as primary versus backup.

### from `deep_consensus`
- **quorum_read** (d1): Reading from sufficient replicas to guarantee seeing latest write.
- **quorum_write** (d1): Writing to sufficient replicas to guarantee subsequent readers see the value.
- **replication_factor** (d1): Count of replica copies maintained for durability and availability.
- **strong_quorum** (d1): Quorum where read and write quorums overlap (r + w > n).

### from `deep_raft`
- **a007** (d3): Quorum in agreement: a subset of processes sufficient to guarantee agreement can be reached, typically intersecting any valid quorum to ensure overlap.
- **a008** (d3): Threshold in agreement: the minimum number of correct processes required to guarantee safety and liveness under given failure assumptions.
- **a009** (d4): Asymmetric agreement: one class of processes (e.g., primary) must agree while another class (e.g., backups) may reach different decisions, used in primary-backup protocols.
- **a002** (d4): Validity in agreement: the decided value must have been proposed by some process in the system, guaranteeing agreements are grounded in actual proposals.
- **a005** (d5): Uniform agreement: all processes including those that later fail must decide on the same value, stricter than ordinary agreement which only binds correct processes.
- **a004** (d5): Termination in agreement: every correct process eventually decides some value, ensuring the protocol makes progress and does not stall indefinitely.

### from `distributed_consensus_and_replication_protocols`
- **linearizability** (d1): Strongest consistency model: every operation appears atomic and ordered in real time across all nodes.
- **semi_synchronous_replication** (d1): Write waits for quorum of replicas to acknowledge; balances latency and durability.
- **synchronous_replication** (d1): Write waits for all replicas to acknowledge before returning to client.
- **consensus** (d2): Agreement on a single value among a set of distributed processes; the core problem consensus protocols solve.
- **fault_tolerance** (d3): System's ability to continue operating correctly despite component failures.
- **replicated_log** (d4): Ordered log of commands maintained across replicas; foundation of state machine replication.

## CONSUMERS (what needs this)
`cap_consistency`, `cassandra`, `dynamo`, `flexible_quorum`, `grid_quorum`, `split_brain`

---
*Projected from the `distributed consensus and replication protocols` KB (196 concepts / 187 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
