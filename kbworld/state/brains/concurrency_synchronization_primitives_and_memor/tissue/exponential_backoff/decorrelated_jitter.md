# decorrelated_jitter

[deep_spinlock · d2] Jitter strategy where each thread computes delay = random.uniform(min_delay, previous_delay * 3); history-dependent decorrelation reduces coordinated retry waves.
