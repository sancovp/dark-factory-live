# Market Maker Recipe

**Type:** Recipe
**Rarity:** Epic
**Composes:** market_diversity_lens + rarity_guard_lens + chain_verifier_recipe

## Purpose
Automated market-maker: gap-first, then craft-to-fill.

## Pipeline
1. market_diversity_lens: find gaps
2. rarity_guard_lens: determine rarity
3. chain_verifier_recipe: verify quality
4. Execute trade_post with dynamic pricing
