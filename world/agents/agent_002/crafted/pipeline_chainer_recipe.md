# Pipeline Chainer Recipe

## Type: recipe

## Description
Composes two or more skills into a sequential pipeline where output of one feeds input of the next. Enforces typed handoffs and halts on first failure with a diagnostic report.

## Inputs
- `pipeline_steps`: Ordered list of skill paths (min 2)
- `initial_payload`: Initial input to first step

## Outputs
- `pipeline_output`: Final result after all steps
- `step_results`: Per-step outputs for inspection
- `failure_report`: Diagnostic if any step fails

## Recipe

```python
"""
Pipeline Chainer Recipe
Chains skills in sequence, passing outputs forward.
"""

from typing import Any
import json

def run_pipeline(steps: list[str], initial_payload: Any) -> dict:
    """
    Args:
        steps: List of skill file paths in execution order
        initial_payload: Starting data for step 1
    Returns:
        dict with pipeline_output, step_results, failure_report
    """
    if len(steps) < 2:
        return {
            "pipeline_output": None,
            "step_results": [],
            "failure_report": "Pipeline requires at least 2 steps"
        }
    
    step_results = []
    current_payload = initial_payload
    
    for i, step in enumerate(steps):
        try:
            result = execute_skill(step, current_payload)
            step_results.append({
                "step": i + 1,
                "skill": step,
                "status": "pass",
                "output": result
            })
            current_payload = result
        except Exception as e:
            return {
                "pipeline_output": None,
                "step_results": step_results,
                "failure_report": f"Step {i+1} ({step}) failed: {str(e)}"
            }
    
    return {
        "pipeline_output": current_payload,
        "step_results": step_results,
        "failure_report": None
    }


def execute_skill(skill_path: str, payload: Any) -> Any:
    """
    Load and execute a skill by path.
    Placeholder — replace with actual skill runner.
    """
    return payload


# CLI interface
if __name__ == "__main__":
    import sys
    if len(sys.argv) < 3:
        print("Usage: pipeline_chainer.py <step1> <step2> [...stepN]> <payload>")
        sys.exit(1)
    
    steps = sys.argv[1:-1]
    payload_raw = sys.argv[-1]
    
    try:
        payload = json.loads(payload_raw)
    except json.JSONDecodeError:
        payload = payload_raw
    
    result = run_pipeline(steps, payload)
    print(json.dumps(result, indent=2))


# Example pipeline composition:
# Step 1: dependency_audit_lens  — scans a skill for missing deps
# Step 2: chain_verifier_recipe  — validates the composition chain
#
# Usage: run_pipeline(
#     steps=["crafted/dependency_audit_lens.md", "crafted/chain_verifier_recipe.md"],
#     initial_payload={"target_skill": "crafted/my_skill.md"}
# )
# → output = verified pipeline result
