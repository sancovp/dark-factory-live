# current_delay

[deep_spinlock · d1] The computed wait interval for the current retry iteration; derived from base_delay multiplied by backoff_multiplier raised to the iteration count, then capped by delay_ceiling.
