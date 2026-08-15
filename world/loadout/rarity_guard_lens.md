# Rarity Guard Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Detect rarity inflation and verify skill-to-rarity alignment

## Rarity Thresholds

| Rarity | Composition Requirement |
|--------|-------------------------|
| Common | Single concept, no dependencies |
| Uncommon | 1-2 concepts OR composes 1 other skill |
| Rare | Composes 2+ skills into pipeline |
| Epic | Novel combination creating emergent capability |

## Verdict Summary (patch-5 audit)

| Skill | Claimed | Verdict |
|-------|---------|---------|
| chain_verifier_recipe.md | Rare | UPHOLD |
| trade_safety_recipe.md | Rare | UPHOLD |
| loadout_dependency_proof_recipe.md | ~~Epic~~ Rare | DOWNGRADED |
| inversion_second_order_recipe.md | ~~Epic~~ Rare | DOWNGRADED |
| dependency_trace_lens.md | Uncommon | UPHOLD |
