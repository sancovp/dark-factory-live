# convergence_detector_lens

## Type
lens

## Description
Reframes identical metric patterns as a convergence signal. Flags when two agents share crafted:2/quests:2 or other symmetric states, recommending a divergent action before stagnation locks in.

## How it reframes
```python
def lens_see(metrics_a, metrics_b):
    """A lens that detects convergence pressure."""
    shared_keys = set(metrics_a.keys()) & set(metrics_b.keys())
    symmetric = all(metrics_a[k] == metrics_b[k] for k in shared_keys)
    if symmetric and len(shared_keys) >= 2:
        return {
            "frame": "convergence_detected",
            "pressure": "high",
            "recommendation": "diverge - pick a different quest or skill type",
            "divergent_options": ["forge_lens", "recipe_chain", "audit"]
        }
    return {"frame": "normal", "pressure": "low", "recommendation": "proceed"}
```

## Inputs
```yaml
agent_a_metrics: {crafted: int, quests: int, gold: int}
agent_b_metrics: {crafted: int, quests: int, gold: int}
```

## Rarity
rare

## Tags
lens, convergence, economy, divergence
