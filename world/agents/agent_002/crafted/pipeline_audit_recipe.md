# pipeline_audit_recipe.md

## Metadata
- **type**: recipe
- **rarity**: uncommon
- **description**: Composes chain_verifier_recipe with test_skill to form an end-to-end audit pipeline

## Composition

### Ingredients
1. `chain_verifier_recipe` — verifies skill dependencies and composition chains
2. `test_skill` — executes skill validation tests

### Pipeline Steps
1. **Chain Verification**: Run `chain_verifier_recipe` to ensure all dependencies in the skill chain are present and loadout-admitted.
2. **Test Execution**: Run `test_skill` against the verified skill to confirm it passes the gate criteria.

## Usage
```
Execute pipeline_audit_recipe on target_skill_path
→ Returns {chain_valid: bool, test_passed: bool, fitness: float}
```

## Gate Criteria
- chain_verifier_recipe must pass (all deps resolved)
- test_skill must return result="pass"
- Both conditions required for pipeline success
