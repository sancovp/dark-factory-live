# Inversion-Chain Verification Pipeline

## Type: recipe

## Description
A pipeline recipe that chains second_order_inversion_lens with chain_verifier_recipe to validate composed skills end-to-end.

## Ingredients
- second_order_inversion_lens (lens)
- chain_verifier_recipe (recipe)

## Procedure

### Phase 1: Inversion Analysis
Apply second_order_inversion_lens to identify:
- Hidden assumptions in the target skill composition
- Inverted dependencies that may cause divergence
- Second-order effects of the proposed chain

### Phase 2: Chain Verification
Use chain_verifier_recipe to:
- Verify all dependency links in the composition
- Confirm each chain link passes its gate criteria
- Validate composition produces expected output

### Phase 3: Synthesis
Combine findings into a verification report:
- Confirmed chain links (convergence)
- Problematic links requiring revision (divergence)
- Recommended fixes for broken links

## Output
A verified pipeline with documented convergence points and flagged divergence.

## Rarity: rare
