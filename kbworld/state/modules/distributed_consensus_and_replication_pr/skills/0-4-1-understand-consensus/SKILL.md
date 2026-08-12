---
name: 0.4.1-understand-consensus
description: "[0.4.1] Agreement on a single value among a set of distributed processes; the core problem consensus protocols solve."
---

# understand-consensus

**CALL NUMBER:** `distributed_consensus_and_replication_protocols.consensus : deep_raft(6)`
**DEFINITION:** Agreement on a single value among a set of distributed processes; the core problem consensus protocols solve.

Invoke this skill to understand `consensus` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **agreement** (d1): The property that a set of distributed processes reach the same decision outcome on a given value. Uniform agreement requires all processes including those that later crash to decide identically; asymmetric agreement permits different decision classes for different process roles such as primary versus backup.

### from `deep_raft`
- **a007** (d1): Quorum in agreement: a subset of processes sufficient to guarantee agreement can be reached, typically intersecting any valid quorum to ensure overlap.
- **a008** (d1): Threshold in agreement: the minimum number of correct processes required to guarantee safety and liveness under given failure assumptions.
- **a009** (d2): Asymmetric agreement: one class of processes (e.g., primary) must agree while another class (e.g., backups) may reach different decisions, used in primary-backup protocols.
- **a002** (d2): Validity in agreement: the decided value must have been proposed by some process in the system, guaranteeing agreements are grounded in actual proposals.
- **a005** (d3): Uniform agreement: all processes including those that later fail must decide on the same value, stricter than ordinary agreement which only binds correct processes.
- **a004** (d3): Termination in agreement: every correct process eventually decides some value, ensuring the protocol makes progress and does not stall indefinitely.

### from `distributed_consensus_and_replication_protocols`
- **fault_tolerance** (d1): System's ability to continue operating correctly despite component failures.
- **replicated_log** (d2): Ordered log of commands maintained across replicas; foundation of state machine replication.

## CONSUMERS (what needs this)
`a005`, `a009`, `atomic_broadcast`, `causal_consistency`, `ft005`, `ft007`, `ft009`, `ft014`, `ft016`, `ft017`, `linearizability`, `lock_free`, `obstruction_free`, `paxos`, `raft`, `sequential_consistency`, `two_phase_commit`, `viewstamped_replication`, `wait_free`, `zab`

---
*Projected from the `distributed consensus and replication protocols` KB (196 concepts / 187 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
