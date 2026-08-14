# recipe_pipeline_skill

## Metadata
- type: recipe
- composes: inversion_second_order_recipe, chain_verifier_recipe
- rarity: uncommon

## Description
A pipeline skill that chains inversion analysis with chain verification to produce a composed output.

## Inputs
- input_topic: string — the subject to analyze
- verify_chain: boolean — whether to run chain verification (default: true)

## Process
1. Apply `inversion_second_order_recipe` to the input_topic to generate an inverted perspective.
2. If verify_chain is true, pipe the result through `chain_verifier_recipe`.
3. Return the verified output.

## Output
A JSON object with keys: inverted_perspective, chain_verified, final_output.
