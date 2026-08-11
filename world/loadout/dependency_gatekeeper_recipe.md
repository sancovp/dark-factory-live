# Dependency Gatekeeper Recipe

## Type
recipe

## Rarity
rare

## Description
Verifies a skill's declared dependencies exist in loadout before allowing it to be listed as loadout-ready. Composes dependency_lens analysis with test_skill validation to prevent the dependency_proof_before_loadout failure mode.

## Problem This Solves
Standing rule dependency_proof_before_loadout: "A skill that imports or references other components requires proof those dependencies exist in loadout BEFORE installation." Many skills claim to compose others but don't verify those components exist, leading to gate failures.

## Composes
1. dependency_lens - analyzes a skill file for references to other skills/components
2. test_skill - validates the dependency check itself works correctly

## Pipeline Protocol

### Stage 1: Dependency Discovery (uses dependency_lens)
- Parse the target skill file for dependency references
- Look for patterns: "composes X", "uses skill Y", "imports Z"
- Build a list of declared dependencies

### Stage 2: Loadout Verification
- For each declared dependency, check if it exists in:
  - loadout/ (loadout skills)
  - crafted/ (available crafted skills)
- Mark each as: FOUND | MISSING | AMBIGUOUS

### Stage 3: Validation (uses test_skill)
- Run the dependency check itself through test_skill
- Confirm it produces correct verdicts for:
  - A skill with all deps present → PASS
  - A skill with missing deps → FAIL with specific missing list

### Stage 4: Gatekeeper Verdict
```
## Dependency Gatekeeper Report

Target Skill: [skill_path]
Declared Dependencies: [list]
Found: [list]
Missing: [list]
Verdict: [LOADOUT_READY | INCOMPLETE | UNVERIFIABLE]
```

## Usage
Input: skill_path to verify
Output: dependency_gatekeeper_report with verdict

## Quality Criteria
- Identifies ALL declared dependencies (no missed references)
- Correctly distinguishes FOUND vs MISSING vs AMBIGUOUS
- The validation stage itself must pass test_skill
- Report is actionable: a failed skill can be fixed by installing missing deps

## Why This Improves The Repo
Prevents the guard_must_pass_gate_to_be_loadout failure: a dependency gatekeeper that fails its own gate is worse than no gatekeeper. By composing test_skill validation, this recipe verifies itself before declaring other skills ready.
