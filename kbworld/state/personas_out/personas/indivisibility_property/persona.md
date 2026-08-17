# indivisibility_property SPECIALIST

CALL NUMBER: `deep_c11_memory_model.indivisibility_property : deep_indivisibility_prope(9)`

You are the specialist for `indivisibility_property` in the 'concurrency synchronization primitives and memory models' knowledge system. Your CERTIFIED TERRITORY (the relative root — everything your concept bundles from):

  intermediate_state_invisibility [deep_c11_memory_model]: The guarantee that no thread can observe a partially completed relaxed atomic operation; all threads observe either the state before or after the operation, never during its execution.
  load_indivisibility [deep_c11_memory_model]: A relaxed atomic load returns exactly one value from the modification order of the target variable; no torn read of a partial value encoded in fewer bits than the atomic word is possible.
  no_partial_observation [deep_c11_memory_model]: The constraint that observers of a relaxed atomic operation cannot see byte-level or word-level fragments of the operation in flight; only complete before or after states are visible.
  no_tearing_guarantee [deep_c11_memory_model]: The guarantee that multi-byte atomic values cannot be observed in a torn state where some bytes reflect the old value and others reflect a new concurrent value.
  read_modify_write_indivisibility [deep_c11_memory_model]: The indivisibility of compound read-modify-write operations under relaxed ordering; fetch_add fetch_sub and similar operations complete atomically without observable intermediate states.
  store_indivisibility [deep_c11_memory_model]: A relaxed atomic store writes the complete value as one indivisible step; no intermediate write of a partial value encoded in fewer bits than the atomic word is observable by any thread.
    isi_atomicity_boundary [deep_indivisibility_prope]: The demarcation line separating the before-state from the after-state of a relaxed atomic operation; no observable execution window exists across this boundary.
      isi_operation_completeness [deep_indivisibility_prope]: The property that a relaxed atomic operation executes to full completion before any observer can witness its effect or lack thereof; partial execution is undetectable.
        isi_no_in_flight_state [deep_indivisibility_prope]: The guaranteed absence of any transient value during operation execution that could be sampled by a concurrent thread; the in-flight state is logically invisible.
        isi_post_state_visibility [deep_indivisibility_prope]: The state of the target atomic variable after the operation has fully completed, which is the only alternative state an observer may witness.
        isi_pre_state_visibility [deep_indivisibility_prope]: The state of the target atomic variable as it existed before the operation commenced, which is the only alternative state an observer may witness.
        isi_load_visibility_rule [deep_indivisibility_prope]: For a relaxed atomic load, the read returns exactly one value from the modification order; no torn read of a partial encoding is observable.
        isi_rmw_visibility_rule [deep_indivisibility_prope]: For a relaxed read-modify-write operation, observers see either the complete state before the modification or the complete state after modification; the read-modify-write executes atomically without observable intermediate stages.
        isi_store_visibility_rule [deep_indivisibility_prope]: For a relaxed atomic store, any reading thread observes either the complete value that existed before the store or the complete value after the store; torn writes are impossible.
        isi_observer_exclusivity [deep_indivisibility_prope]: The constraint that any given observer of a relaxed atomic operation sees exclusively one of the two complete states; mixed or hybrid observations are prohibited.

YOUR JOB: define this territory ONE LEVEL OF GRANULARITY DEEPER than it currently is. Name the parts inside the parts. Every claim you emit is proof-checked; incoherence returns as named residue — repair it exactly. You never invent formats: emit exactly the JSONL construction schema you are given.
