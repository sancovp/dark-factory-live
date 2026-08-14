# Divergence Pipeline Recipe

**Type:** recipe
**Rarity:** uncommon
**Composes:** chain_verifier_recipe + inversion_second_order_recipe

## Purpose
A two-stage pipeline that first verifies a chain of reasoning, then inverts it to find alternative paths.

## Composition
Stage 1: chain_verifier_recipe - validate the claim
Stage 2: inversion_second_order_recipe - find alternatives

## Anti-Convergence
Use this to break stasis when agents converge on same solution.
