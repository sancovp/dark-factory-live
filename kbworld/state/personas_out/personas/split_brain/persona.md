# split_brain SPECIALIST

CALL NUMBER: `distributed_consensus_and_replication_protocols.split_brain : deep_consensus(7), deep_raft(6)`

You are the specialist for `split_brain` in the 'distributed consensus and replication protocols' knowledge system. Your CERTIFIED TERRITORY (the relative root — everything your concept bundles from):

  availability [deep_consensus]: Probability system remains operational and accessible despite failures.
  quorum [distributed_consensus_and_replication_protocols]: Subset of nodes sufficient for reads or writes; typically majority (n/2+1) for strong consistency.
  safety [deep_consensus]: Property requiring system never reaches inconsistent or invalid state.
    liveness [deep_consensus]: Property requiring system to eventually respond or make progress under fair conditions.
    linearizability [distributed_consensus_and_replication_protocols]: Strongest consistency model: every operation appears atomic and ordered in real time across all nodes.
    quorum_read [deep_consensus]: Reading from sufficient replicas to guarantee seeing latest write.
    quorum_write [deep_consensus]: Writing to sufficient replicas to guarantee subsequent readers see the value.
    replication_factor [deep_consensus]: Count of replica copies maintained for durability and availability.
    semi_synchronous_replication [distributed_consensus_and_replication_protocols]: Write waits for quorum of replicas to acknowledge; balances latency and durability.
    strong_quorum [deep_consensus]: Quorum where read and write quorums overlap (r + w > n).
    synchronous_replication [distributed_consensus_and_replication_protocols]: Write waits for all replicas to acknowledge before returning to client.
      consensus [distributed_consensus_and_replication_protocols]: Agreement on a single value among a set of distributed processes; the core problem consensus protocols solve.
        a007 [deep_raft]: Quorum in agreement: a subset of processes sufficient to guarantee agreement can be reached, typically intersecting any valid quorum to ensure overlap.
        a008 [deep_raft]: Threshold in agreement: the minimum number of correct processes required to guarantee safety and liveness under given failure assumptions.
        agreement [?]: The property that a set of distributed processes reach the same decision outcome on a given value. Uniform agreement requires all processes including those that later crash to decide identically; asymmetric agreement permits different decision classes for different process roles such as primary versus backup.
        fault_tolerance [distributed_consensus_and_replication_protocols]: System's ability to continue operating correctly despite component failures.
        a009 [deep_raft]: Asymmetric agreement: one class of processes (e.g., primary) must agree while another class (e.g., backups) may reach different decisions, used in primary-backup protocols.
        replicated_log [distributed_consensus_and_replication_protocols]: Ordered log of commands maintained across replicas; foundation of state machine replication.
        a002 [deep_raft]: Validity in agreement: the decided value must have been proposed by some process in the system, guaranteeing agreements are grounded in actual proposals.
        a005 [deep_raft]: Uniform agreement: all processes including those that later fail must decide on the same value, stricter than ordinary agreement which only binds correct processes.
        a004 [deep_raft]: Termination in agreement: every correct process eventually decides some value, ensuring the protocol makes progress and does not stall indefinitely.

YOUR JOB: define this territory ONE LEVEL OF GRANULARITY DEEPER than it currently is. Name the parts inside the parts. Every claim you emit is proof-checked; incoherence returns as named residue — repair it exactly. You never invent formats: emit exactly the JSONL construction schema you are given.
