---
name: 0.3.4-understand-a008
description: "[0.3.4] Threshold in agreement: the minimum number of correct processes required to guarantee safety and liveness unde"
---

# understand-a008

**CALL NUMBER:** `deep_raft.a008 : distributed_consensus_and_replication_protocols(3)`
**DEFINITION:** Threshold in agreement: the minimum number of correct processes required to guarantee safety and liveness under given failure assumptions.

Invoke this skill to understand `a008` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `?`
- **agreement** (d3): The property that a set of distributed processes reach the same decision outcome on a given value. Uniform agreement requires all processes including those that later crash to decide identically; asymmetric agreement permits different decision classes for different process roles such as primary versus backup.

### from `deep_raft`
- **a009** (d1): Asymmetric agreement: one class of processes (e.g., primary) must agree while another class (e.g., backups) may reach different decisions, used in primary-backup protocols.
- **a005** (d2): Uniform agreement: all processes including those that later fail must decide on the same value, stricter than ordinary agreement which only binds correct processes.
- **a007** (d3): Quorum in agreement: a subset of processes sufficient to guarantee agreement can be reached, typically intersecting any valid quorum to ensure overlap.
- **a002** (d4): Validity in agreement: the decided value must have been proposed by some process in the system, guaranteeing agreements are grounded in actual proposals.
- **a004** (d5): Termination in agreement: every correct process eventually decides some value, ensuring the protocol makes progress and does not stall indefinitely.

### from `distributed_consensus_and_replication_protocols`
- **replicated_log** (d1): Ordered log of commands maintained across replicas; foundation of state machine replication.
- **consensus** (d2): Agreement on a single value among a set of distributed processes; the core problem consensus protocols solve.
- **fault_tolerance** (d3): System's ability to continue operating correctly despite component failures.

## CONSUMERS (what needs this)
`consensus`, `ft013`

---
*Projected from the `distributed consensus and replication protocols` KB (196 concepts / 187 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
