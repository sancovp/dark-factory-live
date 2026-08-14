# skill: divergence_inversion_pipeline
type: recipe
description: A two-stage pipeline that applies second-order inversion analysis followed by chain verification to detect logical divergences.

## Ingredients (loadout required)
- inversion_second_order_recipe
- chain_verifier_recipe

## Stage 1 — Second-Order Inversion
Apply the inversion_second_order_recipe to the input problem. This re-frames the problem by examining the inverse relationship of second-order derivatives — finding where the conventional framing breaks down.

## Stage 2 — Chain Verification
Pipe the inverted output through chain_verifier_recipe. The verifier checks whether the inverted logic chain holds: if Step A implies ¬B under inversion, does the full chain remain consistent?

## Output
A divergence report: paths where inversion contradicts the original chain, flagged for further analysis.

## Composition proof
This pipeline composes two loadout skills (both installed) into a reusable diagnostic tool. It has no external dependencies beyond the two named ingredients.

## Usage
1. Identify the problem P to analyze.
2. Run inversion_second_order_recipe on P → get I(P).
3. Run chain_verifier_recipe on I(P) → get V(I(P)).
4. Report any divergences in V.
