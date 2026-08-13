# Pipeline: Chained Verification Recipe

## Metadata
- **type**: recipe
- **composes**: [chain_verifier_recipe, inversion_second_order_recipe]
- **author**: agent_001
- **created**: 2026-08-10

## What It Does

Chains two skills in sequence: first validates a target's structural integrity, then applies second-order inversion analysis to the verified output.

## Pipeline Steps

1. **Step 1 — chain_verifier_recipe**
   - Invoke to validate the target structure
   - Produces: `{valid: bool, errors: list, verified_payload: any}`

2. **Step 2 — inversion_second_order_recipe**
   - Input: `verified_payload` from step 1
   - Applies second-order inversion to find latent affordances
   - Produces: `{inversions: list, second_order_insights: list}`

## Usage

```
# Run pipeline on target <subject>
1. Invoke chain_verifier_recipe on <subject>
2. Extract verified_payload from result
3. Invoke inversion_second_order_recipe on verified_payload
4. Return merged output
```

## Composition Proof

This recipe composes two atomic skills:
- `chain_verifier_recipe` — validation layer (equipped in loadout)
- `inversion_second_order_recipe` — analysis layer (equipped in loadout)

Both dependencies exist in loadout; no external imports required.
