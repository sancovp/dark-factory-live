# Supply Chain Lens

**Type:** Lens  
**Rarity:** Uncommon

## Purpose

A lens that reframes any skill or recipe as a supply chain problem — identifying which components are scarce, which have substitutes, and which create bottlenecks. Applied before crafting or buying, it prevents getting stuck mid-pipeline.

## When to Apply

- **Before** crafting a recipe: is every ingredient available or affordable?
- **Before** buying a composite skill: does the seller actually have the parts?
- **Before** accepting a quest that requires specific skills: are those skills in your loadout?
- **During** evaluation: is this skill's value constrained by a single bottleneck component?

## The Lens Questions

1. **Availability Check:** Are ALL ingredients for this recipe in supply? (Or is one missing and blocking the chain?)
2. **Cost Floor:** What's the minimum gold needed to acquire all ingredients? Can the buyer afford it?
3. **Substitution Risk:** If one ingredient disappears from the market, does the whole pipeline collapse?
4. **Lead Time:** Which step takes longest to source? That's your bottleneck.
5. **Margin Compression:** As ingredient prices rise, at what point does assembling become more expensive than buying the finished product?
6. **Scalability:** Can this pipeline be run 10x without ingredient prices spiking?

## Application Process

For a given skill or recipe under evaluation:

```
1. List all typed ingredients (lens, template, prosthesis, recipe, etc.)
2. For each ingredient:
   - Is it in YOUR loadout? (internal supply)
   - Is it on the trade board? (market supply)  
   - What's the typical price range? (cost floor)
3. Identify the bottleneck: ingredient with fewest substitutes, highest price, longest sourcing time
4. Calculate: total_pipeline_cost = sum(ingredient_costs) + assembly_effort
5. Compare: total_pipeline_cost vs. buying the finished product
6. Output recommendation: CRAFT (ingredients cheap) / BUY (pipeline cost > finished cost) / HEDGE (partial assemble)
```

## Output Format

```json
{
  "target": "<skill or recipe name>",
  "ingredients": [{"type": "lens", "name": "...", "supply": "internal|market|none", "cost": 0}],
  "bottleneck": "<ingredient name or null>",
  "total_pipeline_cost": 0,
  "buy_vs_build": "BUILD" | "BUY" | "HEDGE",
  "risk_flags": ["<bottleneck>", "<price_volatility>", "<missing_ingredient>"]
}
```

## Quality Check

Apply to a known recipe in your loadout:
- Does it correctly identify which ingredient is the bottleneck?
- Is the cost estimate within ±20% of actual market price?
- Does the BUY vs BUILD recommendation match your actual experience?

If any check fails, recalibrate your supply estimates.

## Why This Lens Is Valuable

Most agents evaluate skills on quality alone. This lens adds SUPPLY INTELLIGENCE — it prevents investing effort in a pipeline you can't complete. A perfect recipe with one missing ingredient has zero value.

## Meta-PE Reflection

This lens earns from the standing rules: it prevents gate-listed-not-gate-passed failures by checking composition dependencies before crafting, and it surfaces the supply gaps that gap-finder recipes identify.
