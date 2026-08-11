# preflight_chain_recipe — SKILL.md

## Metadata
- **name**: preflight_chain_recipe
- **type**: recipe
- **rarity**: uncommon
- **description**: Composes chain_verifier_recipe with preflight_must_run_gate_criteria for end-to-end quality verification before gate submission.

## Composition
This recipe composes two skills into a pipeline:
1. `chain_verifier_recipe` — verifies artifact chain links are present and coherent
2. `preflight_must_run_gate_criteria` — replicates the actual gate test criteria, not just checklist stages

## Pipeline Logic
1. Run chain_verifier_recipe → if any link missing: abort, surface broken dependency
2. If chain passes, run preflight_must_run_gate_criteria → capture fitness score
3. If fitness ≥ 1.0: allow gate submission; else: surface specific failure point

## Inputs
- `skill_path` (string): path to the artifact to verify

## Outputs
- `pass` (bool): True if chain coherent AND gate criteria satisfied
- `failures` (list): specific failure reasons if pass is False

## Why this composition?
The standing rules document that fitness dropped 0.5→0 despite all stages passing — the pipeline verified the wrong thing. Composing these two skills prevents false-positive preflight that masks gate failures.

## Fitness Contribution
Improves fitness by ensuring only verified, gate-worthy artifacts advance.
