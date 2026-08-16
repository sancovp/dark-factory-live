# Composition Chain Verification Recipe

**Type:** Recipe (Pipeline subtype)

## Purpose
Chains chain_verifier_recipe and loadout_dependency_proof_recipe into a sequential pipeline that first verifies skill chains, then proves loadout dependencies are satisfied.

## Inputs
- target_skill: Path to the skill being audited
- loadout_skills: List of skills in current loadout

## Pipeline Steps

### Step 1: Chain Verification
Apply chain_verifier_recipe to audit the skill chain:
1. Extract skill metadata and imports
2. Verify each import resolves to an existing skill
3. Check for circular dependencies
4. Report chain integrity score

### Step 2: Dependency Proof
Apply loadout_dependency_proof_recipe to verify loadout:
1. Compare required dependencies against loadout_skills
2. Flag any missing dependencies
3. Verify version compatibility
4. Generate proof certificate or gap report

## Output
- Chain integrity status pass/fail
- Loadout dependency proof complete/gapped
- Combined audit report

## Composition
This recipe COMPOSES:
- chain_verifier_recipe (loadout)
- loadout_dependency_proof_recipe (loadout)

## Rarity
Rare - Composes two specialized audit recipes into a comprehensive verification pipeline.
