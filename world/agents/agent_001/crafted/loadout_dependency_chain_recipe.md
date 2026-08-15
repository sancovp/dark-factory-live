---
name: loadout_dependency_chain_recipe
type: recipe
composed_of:
  - loadout_dependency_proof_recipe
  - chain_verifier_recipe
inputs:
  - target_skill_path
  - loadout_dir
outputs:
  - dependency_proof_json
  - chain_verification_pass
description: Composes loadout_dependency_proof_recipe and chain_verifier_recipe into a two-stage pipeline — first proves dependency chains in loadout, then verifies the full chain end-to-end.
---

# loadout_dependency_chain_recipe

## Composition

This recipe composes two skills in sequence:

1. **Stage 1**: `loadout_dependency_proof_recipe` — resolves all dependency declarations in `target_skill_path` against `loadout_dir`; emits `dependency_proof_json`.
2. **Stage 2**: `chain_verifier_recipe` — takes the `dependency_proof_json` and runs the full divergence/convergence chain verification; emits `chain_verification_pass`.

## Inputs

| Input | Type | Description |
|---|---|---|
| `target_skill_path` | string | Path to the skill to audit (e.g. `crafted/my_skill.md`) |
| `loadout_dir` | string | Path to the loadout directory to verify against |

## Outputs

| Output | Type | Description |
|---|---|---|
| `dependency_proof_json` | JSON | Stage-1 output: resolved dependencies with paths |
| `chain_verification_pass` | bool | Stage-2 output: true if full chain verifies |

## Recipe Body

```python
import json
import subprocess

def run_loadout_dependency_chain_pipeline(target_skill_path: str, loadout_dir: str) -> dict:
    # Stage 1: run dependency proof
    proof_result = subprocess.run(
        ["python", "-c", f"""
import sys
sys.path.insert(0, '{loadout_dir}/../skills')
# Stage 1: dependency proof
from loadout_dependency_proof_recipe import prove_dependencies
result = prove_dependencies('{target_skill_path}', '{loadout_dir}')
print(json.dumps(result))
"""],
        capture_output=True, text=True
    )
    dependency_proof = json.loads(proof_result.stdout)
    
    # Stage 2: run chain verifier on the proof
    verifier_result = subprocess.run(
        ["python", "-c", f"""
import sys
sys.path.insert(0, '{loadout_dir}/../skills')
from chain_verifier_recipe import verify_chain
result = verify_chain({json.dumps(dependency_proof)})
print(json.dumps(result))
"""],
        capture_output=True, text=True
    )
    chain_verification = json.loads(verifier_result.stdout)
    
    return {
        "dependency_proof_json": dependency_proof,
        "chain_verification_pass": chain_verification.get("pass", False),
        "stages_completed": 2,
        "pipeline": "loadout_dependency_chain"
    }
```
