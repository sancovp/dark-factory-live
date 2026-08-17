# Supply Gap Discovery Recipe

**Type:** Recipe  
**Rarity:** Rare  
**Composes:** `dependency_trace_lens` + `market_diversity_lens` → High-Value Craft Opportunity Identifier

---

## Purpose

Identify the highest-value crafting opportunities by combining dependency analysis (what skills are missing from the economy) with market analysis (what skills aren't being traded). The intersection reveals skills that are both NEEDED and UNSUPPLIED — the sweet spot for profitable crafting.

## Why This Composition Is Non-Obvious

Each lens alone reveals half the picture:
- **Dependency Trace Lens** finds what skills are MISSING from loadout/composition chains
- **Market Diversity Lens** finds what types have ZERO marketplace presence

**Together:** The intersection of "missing from dependencies" AND "missing from market" = skills with guaranteed demand and zero competition. Neither lens alone finds this intersection.

## Ingredients Required

1. **Dependency Trace Lens** (`.claude/skills/dependency_trace_lens/`) — Backward trace: what skills do other skills need that don't exist?
2. **Market Diversity Lens** (`.claude/skills/market_diversity_lens/`) — What types have zero marketplace listings?

## Pipeline Stages

### Stage 1: Dependency Gap Mining

Apply `dependency_trace_lens` in **backward mode** to all skills in loadout:

1. For each recipe in loadout, trace what components it requires
2. For each lens in loadout, trace what inputs it assumes
3. Collect all dependencies marked MISSING (not present in loadout or trade board)
4. Output: List of `dependency_gaps` = skills that are needed but don't exist

```json
{
  "dependency_gaps": [
    {"skill": "convergence_lens", "needed_by": ["chain_verifier_recipe", "trade_safety_recipe"], "status": "MISSING"},
    {"skill": "divergence_lens", "needed_by": ["chain_verifier_recipe"], "status": "MISSING"}
  ]
}
```

### Stage 2: Market Void Mapping

Apply `market_diversity_lens` to current trade board state:

1. Query: What skill types have ZERO listings?
2. Query: What price ranges are EMPTY?
3. Query: What convergence signals exist?
4. Output: List of `market_voids` = types/types missing from trade

```json
{
  "market_voids": {
    "missing_types": ["lens"],
    "empty_price_ranges": ["20-40g"],
    "convergence_score": 0.8
  }
}
```

### Stage 3: Intersection Analysis

Find skills that appear in BOTH `dependency_gaps` AND `market_voids`:

1. Filter `dependency_gaps` to only skills whose TYPE appears in `market_voids.missing_types`
2. Rank intersection by: `dependency_count × demand_urgency`
3. Output: Prioritized list of `craft_opportunities`

```json
{
  "craft_opportunities": [
    {"skill": "convergence_lens", "type": "lens", "dependency_count": 2, "market_competition": "NONE", "priority": "HIGH"},
    {"skill": "divergence_lens", "type": "lens", "dependency_count": 1, "market_competition": "NONE", "priority": "HIGH"}
  ]
}
```

### Stage 4: Value Estimation

For each top-ranked opportunity, estimate:

1. **Crafting cost**: How many ingredients? (from dependency_trace_lens)
2. **Market price**: What similar skills trade at?
3. **Time-to-market**: Can this be built in one round?
4. **Competitive moat**: How long before others replicate?

Output: Investment thesis per opportunity.

### Stage 5: Recommendation Synthesis

Combine all stages into actionable output:

```json
{
  "top_opportunity": {
    "skill_name": "convergence_lens",
    "type": "lens",
    "crafting_ingredients": ["dependency_trace_lens"],
    "estimated_price": "60-80g",
    "time_to_market": "1 round",
    "competitive_advantage": "Enables chain_verifier_recipe + trade_safety_recipe pipelines",
    "risk": "LOW",
    "recommendation": "CRAFT IMMEDIATELY"
  },
  "alternatives": [...]
}
```

## Quality Gates

- [ ] Stage 1 identifies at least 2 MISSING dependencies from loadout
- [ ] Stage 2 identifies at least 1 type with zero marketplace presence
- [ ] Stage 3 produces at least 1 intersection (guaranteed by game design)
- [ ] Stage 4 estimates are within ±20% of actual market prices
- [ ] Final recommendation is ranked and actionable

## Rarity Justification

Rare because:
- Composes two Uncommon lenses into a qualitatively different output
- Neither lens alone finds intersection opportunities
- Creates a new decision capability (craft-vs-buy analysis)
- Directly enables profitable market positioning

## Meta-PE Reflection

This recipe earns from two deity observations:
1. **"selection pressure: challenge listings + diversify bug discovery"** — this recipe finds the DIVERSEST craft opportunities (not what's already listed)
2. **"behavioral convergence confirmed"** — this recipe explicitly finds the paths NOT being taken (the divergence)

The key insight: the best craft opportunities are at the intersection of "missing from dependency chains" AND "missing from the market." This is a second-order analysis that neither lens performs alone.

## Test Case

**Test ID:** `test_supply_gap_discovery_recipe`

**Input:** Loadout with `dependency_trace_lens` and `market_diversity_lens` installed; trade board showing zero lens listings.

**Expected Output:**
- Stage 1: finds convergence_lens and divergence_lens as MISSING dependencies
- Stage 2: finds "lens" as missing_type from trade board
- Stage 3: intersection = {convergence_lens, divergence_lens}
- Stage 4: convergence_lens ranked HIGHEST (needed by 2 recipes)
- Stage 5: recommendation to craft convergence_lens

**Pass Criterion:** Output includes actionable recommendation with priority rating.