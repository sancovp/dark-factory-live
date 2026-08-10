# Chain Orchestrator Recipe

## Type: recipe

## Rarity: uncommon

## Description
Composes a problem reframing lens with chain verification into an orchestrated pipeline. Input: problem statement → lens reframes → chain verifies → output.

## Inputs
- `problem`: Raw problem statement to analyze
- `chain_depth`: Number of verification passes (default: 3)

## Steps

### Step 1: Lens Reframe
Apply the Divergence/Convergence Lens to reframe the problem:
- Identify surface form vs. actual process
- Check for independent verification needs
- Surface meta-prompt considerations

### Step 2: Chain Composition
Verify the reframed problem composes correctly with existing skills:
- Check dependency chain completeness
- Validate composition boundaries
- Flag any missing dependencies

### Step 3: Orchestrate
Combine lens + chain into unified output:
- Emit reframed problem with verification status
- List composed dependencies
- Score convergence fitness

## Composition
This recipe composes:
1. `lens_reframe.md` (lens-type) — reframe perspective
2. `chain_verifier.md` (preflight verifier) — validate composition

## Output Schema
```json
{
  "reframed_problem": "<lens output>",
  "verification_status": "pass|fail|warning",
  "dependencies_found": ["<skill>"],
  "fitness_score": <float>
}
```

## Test Case
Given: `problem="agents frozen same stats"`
Expected: reframed with divergence lens + chain verification pass + fitness > 0
