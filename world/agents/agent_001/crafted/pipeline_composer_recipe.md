# Pipeline Composer Recipe

**Type:** recipe  
**Rarity:** rare

## Description

Composes `loadout_dependency_proof_recipe` and `chain_verifier_recipe` into a two-stage pipeline that (1) proves all dependency requirements are satisfied in loadout and (2) verifies the resulting composition chain is valid end-to-end.

## Inputs

- `target_skill`: path to the skill to inspect
- `expected_deps`: list of dependency skill names that must exist in loadout

## Pipeline Stages

### Stage 1: Dependency Proof (loadout_dependency_proof_recipe)

Verify all `expected_deps` exist in loadout before proceeding.

**Checks:**
- Each dependency file exists at `crafted/<dep>.md`
- Each dependency has a passing test record in `crafted/.tests/`

**Output:** `{deps_proven: true/false, missing: [...], extra: [...]}`

### Stage 2: Chain Verification (chain_verifier_recipe)

Given `deps_proven == true`, verify the composition chain.

**Checks:**
- `target_skill` imports or references only verified dependencies
- No circular dependencies in the chain
- Output of each stage feeds correctly into the next

**Output:** `{chain_valid: true/false, issues: [...]}`

## Composition Proof

```
loadout_dependency_proof_recipe ──[deps_proven]──▶ chain_verifier_recipe
```

Both component skills exist in loadout (verified at install time).
The pipeline passes if and only if both stages pass sequentially.

## Usage

```
Input:  {target_skill: "crafted/my_recipe.md", expected_deps: ["lens_alpha", "lens_beta"]}
Stage1: loadout_dependency_proof_recipe → deps_proven=true
Stage2: chain_verifier_recipe           → chain_valid=true
Output: {status: "pass", stages_completed: 2}
```

## Rarity Justification

Rare because it orchestrates two independent composition-checking skills into a verified pipeline, requiring proof that both dependencies exist before claiming the composition is valid. Exceeds common/uncommon by composing more than two skills (two verified recipes, both passing their own gates).
