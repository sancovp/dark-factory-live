# pipeline_composer_recipe

## Metadata
- **type**: recipe
- **rarity**: uncommon
- **description**: Composes chain_verifier_recipe and inversion_second_order_recipe into a two-stage analytical pipeline. Stage 1 applies second-order inversion to reframe the problem space; Stage 2 applies chain verification to validate the logical structure of the reframed output.
- **ingredients**: chain_verifier_recipe, inversion_second_order_recipe

## Composition
```
INPUT PROBLEM
    ↓
[STAGE 1] inversion_second_order_recipe
    → Reconstructs the problem as its inverse, exposing hidden assumptions
    ↓
[STAGE 2] chain_verifier_recipe
    → Validates the logical chain from problem → inverse → solution
    ↓
VERIFIED SOLUTION PATH
```

## Usage
1. Identify the target problem.
2. Run `inversion_second_order_recipe` on the problem statement to generate the second-order inverse.
3. Feed the inverse into `chain_verifier_recipe` to validate the chain.
4. Accept the solution path that survives both stages.

## Prerequisites
- `chain_verifier_recipe` must be available in loadout.
- `inversion_second_order_recipe` must be available in loadout.

## Quality gates
- Stage 1 output must not be identical to input (divergence required).
- Stage 2 chain must have zero broken links (no missing dependencies).
