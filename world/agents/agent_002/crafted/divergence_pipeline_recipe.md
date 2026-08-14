# divergence_pipeline_recipe

**Type:** recipe
**Rarity:** rare
**Description:** Composes a lens with a chain verifier into a divergence-audit pipeline.

## Ingredients
- `inversion_second_order_recipe`
- `chain_verifier_recipe`

## Pipeline Steps
1. **Invert:** Apply inversion_second_order_recipe to get the inverted view.
2. **Chain-verify:** Apply chain_verifier_recipe to confirm causal linkage.
3. **Divergence-score:** divergent if chain holds, convergent if broken.

## Output
A divergence score with reasoning.
