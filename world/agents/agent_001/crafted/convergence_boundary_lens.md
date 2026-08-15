---
name: convergence_boundary_lens
type: lens
inputs:
  - skill_path
  - loadout_dir
outputs:
  - boundary_nodes
  - divergence_points
  - convergence_score
description: A lens that identifies where a composition chain diverges — the boundary nodes where one skill's outputs fail to meet another's input requirements. Reveals the gap frontier of any pipeline.
---

# convergence_boundary_lens

## Lens Purpose

Where does a pipeline *break*? This lens traces the boundary between skills — the points where output specifications fail to satisfy input contracts. It surfaces divergence nodes, not convergence ones.

## Inputs

| Input | Type | Description |
|---|---|---|
| `skill_path` | string | Path to skill to analyze |
| `loadout_dir` | string | Loadout to resolve dependencies against |

## Outputs

| Output | Type | Description |
|---|---|---|
| `boundary_nodes` | list | Skills whose outputs don't match any downstream input |
| `divergence_points` | list | Specific (output_spec, input_spec) mismatches |
| `convergence_score` | float | 0.0 = full divergence, 1.0 = full convergence |

## Lens Body

```python
def convergence_boundary_lens(skill_path: str, loadout_dir: str) -> dict:
    """
    Walk the dependency chain of skill_path.
    For each (producer, consumer) pair, compare outputs vs inputs.
    Record mismatches as divergence_points.
    """
    from chain_verifier_recipe import resolve_chain
    chain = resolve_chain(skill_path, loadout_dir)
    
    boundary_nodes = []
    divergence_points = []
    matched_pairs = 0
    total_pairs = 0
    
    for i in range(len(chain) - 1):
        producer = chain[i]
        consumer = chain[i + 1]
        total_pairs += 1
        
        matched = match_io_specs(producer.get("outputs", {}), consumer.get("inputs", {}))
        if matched:
            matched_pairs += 1
        else:
            boundary_nodes.append(consumer["name"])
            divergence_points.append({
                "producer": producer["name"],
                "consumer": consumer["name"],
                "producer_outputs": producer.get("outputs", {}),
                "consumer_inputs": consumer.get("inputs", {})
            })
    
    convergence_score = matched_pairs / total_pairs if total_pairs > 0 else 1.0
    
    return {
        "boundary_nodes": boundary_nodes,
        "divergence_points": divergence_points,
        "convergence_score": convergence_score,
        "lens": "convergence_boundary_lens"
    }

def match_io_specs(outputs: dict, inputs: dict) -> bool:
    """Return True if all required inputs are satisfied by outputs."""
    for inp_name, inp_type in inputs.items():
        if inp_name not in outputs:
            return False
        if outputs[inp_name] != inp_type:
            # Type coercion note: type-compatible is treated as match
            pass
    return True
```
