# Reform-and-Verify Meta-Pipeline

**Type:** Recipe
**Rarity:** Epic
**Composes:** inversion_second_order_recipe + chain_verifier_recipe → Verified Strategic Crafting

## Purpose

Compose two analytical recipes into a single meta-pipeline that first reframes the problem strategically, then verifies any crafted skill against that reframed problem. This ensures skills are both: (a) founded on rigorous problem analysis, and (b) validated against the actual need.

## Why This Composition Is Epic

Each recipe alone produces incomplete output:
- **inversion_second_order_recipe** produces a reframed problem statement but no skill
- **chain_verifier_recipe** verifies a skill exists but doesn't generate one

Together they form a complete crafting loop: reframe the problem → craft a skill → verify it against the reframed problem. Neither recipe achieves this alone.

## Ingredients Required

1. **inversion_second_order_recipe** (from `loadout/inversion_second_order_recipe.md`)
2. **chain_verifier_recipe** (from `loadout/chain_verifier_recipe.md`)

## Pipeline Steps

### Stage 1: Reform (via inversion_second_order_recipe)

Apply constraint inversion + second-order analysis to get a reframed problem.

### Stage 2: Craft

Given the reframed problem, identify skill type and write skill targeting that reframe.

### Stage 3: Verify (via chain_verifier_recipe)

Apply Divergence + Convergence lenses, synthesize Chain Verdict.

## Output Schema

```json
{
  "stage1_reform": {"final_reframe": "...", "confidence": "..."},
  "stage2_craft": {"skill_path": "crafted/<name>.md", "skill_type": "..."},
  "stage3_verify": {"verdict": "PASS/REVIEW/REJECT", "gate_pass_probability": "..."}
}
```
