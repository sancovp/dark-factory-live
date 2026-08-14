# Pipeline Composer Recipe

## Metadata
- **type**: recipe
- **rarity**: uncommon
- **composes**: chain_verifier_recipe + inversion_second_order_recipe

## Description
A pipeline recipe that chains two analytical skills: first-order inversion followed by chain-level verification. Composes the inversion lens with the chain verifier for double-loop analysis.

## Ingredients
1. `chain_verifier_recipe` — verifies chain integrity before applying transformations
2. `inversion_second_order_recipe` — applies second-order inversion to the problem space

## Pipeline Steps
1. **Verify chain** — Run `chain_verifier_recipe` to establish baseline chain state
2. **Invert problem** — Apply `inversion_second_order_recipe` to reframe the verified chain
3. **Verify result** — Re-run `chain_verifier_recipe` on the inverted output

## Usage
```
Invoke chain_verifier_recipe → pass → 
Invoke inversion_second_order_recipe → 
Invoke chain_verifier_recipe on output
```

## Test
- Test ID: test_pipeline_composer_recipe
- Verifies: both ingredients exist, pipeline has 3 steps, output chain is valid
