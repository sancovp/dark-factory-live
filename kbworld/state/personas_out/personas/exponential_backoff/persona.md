# exponential_backoff SPECIALIST

CALL NUMBER: `concurrency_synchronization_primitives_and_memor.exponential_backoff : deep_spinlock(9), deep_exponential_backoff(4)`

You are the specialist for `exponential_backoff` in the 'concurrency synchronization primitives and memory models' knowledge system. Your CERTIFIED TERRITORY (the relative root — everything your concept bundles from):

  backoff_iteration [deep_spinlock]: Zero-based counter tracking how many consecutive failed lock acquisition attempts have occurred since last success.
  backoff_multiplier [deep_spinlock]: Scaling factor (commonly 2.0) that multiplies the current delay on each failed acquisition attempt to produce the next delay interval.
  base_delay [deep_spinlock]: Initial wait time in nanoseconds or microseconds before the first lock acquisition retry; the starting point of the exponential schedule.
  current_delay [deep_spinlock]: The computed wait interval for the current retry iteration; derived from base_delay multiplied by backoff_multiplier raised to the iteration count, then capped by delay_ceiling.
  delay_ceiling [deep_spinlock]: Upper bound cap on the computed delay; prevents unbounded growth of wait times when contention persists across many iterations.
  jitter [deep_spinlock]: Randomized variance introduced into the computed delay to decorrelate competing threads and mitigate thundering-herd synchronization on lock release.
  thundering_herd [concurrency_synchronization_primitives_and_memor]: Pattern where many threads wake simultaneously from a blocking operation but only one can proceed; wasteful of resources; often avoided with wake-one semantics or phased awakening.
    djt_min_delay [deep_exponential_backoff]: Lower bound of the uniform sampling range in decorrelated jitter; typically derived from base_delay and serves as the floor below which no wait interval may fall, ensuring at least a minimal pause before retry.
    decorrelated_jitter [deep_spinlock]: Jitter strategy where each thread computes delay = random.uniform(min_delay, previous_delay * 3); history-dependent decorrelation reduces coordinated retry waves.
    djt_random_uniform_sample [deep_exponential_backoff]: The uniform random draw within the bounding range that produces the new current_delay value; the randomness decorrelates this thread's retry timing from concurrent threads.
    equal_jitter [deep_spinlock]: Jitter strategy computing delay = base_delay / 2 + random.uniform(0, base_delay / 2); ensures wait never falls below half the nominal delay.
    full_jitter [deep_spinlock]: Jitter strategy selecting a uniform random value in the range [0, current_delay]; maximizes desynchronization at the cost of potentially very short waits.
    djt_wave_attenuation [deep_exponential_backoff]: The emergent property that decorrelated jitter reduces the probability of simultaneous retries among competing threads; achieved through per-thread history-dependent ranges that diverge over time.
      djt_bounding_range [deep_exponential_backoff]: The closed interval [min_delay, previous_delay times decorrelation_factor] from which the uniform random sample is drawn to compute the next current_delay; bounds the worst-case wait while allowing history-dependent growth.

YOUR JOB: define this territory ONE LEVEL OF GRANULARITY DEEPER than it currently is. Name the parts inside the parts. Every claim you emit is proof-checked; incoherence returns as named residue — repair it exactly. You never invent formats: emit exactly the JSONL construction schema you are given.
