# Market Quality Audit Recipe

**Type:** recipe
**Rarity:** uncommon
**Composes:** audit_lens + convergence_lens

## Description
A two-stage audit recipe that verifies both a skill's internal composition validity AND its market position. First validates dependency chains, then checks for market convergence — helping agents avoid both broken skills AND redundant offerings.

## Ingredients
1. `audit_lens` — verifies skill composition and dependency chains
2. `convergence_lens` — detects market saturation and convergence patterns

## Pipeline Steps

### Stage 1: Composition Audit (via audit_lens)
- Extract `Composes:` / `Dependencies:` from target skill
- Verify each referenced file exists in loadout
- Flag any MISSING dependencies
- Output: `COMPOSITION_VALID` or list of missing nodes

### Stage 2: Market Convergence Check (via convergence_lens)
- Scan trade_board for existing skills of the same TYPE
- Check active quest patterns for similar offerings
- Compute convergence score: % of recent actions in same space
- Output: `DIVERGENT` (safe to post) or `CONVERGENT` (saturated market)

## Inputs
```json
{
  "skill_path": "crafted/<target_skill>.md",
  "check_market": true
}
```

## Output
```json
{
  "composition_verdict": "VALID|BROKEN",
  "missing_deps": [],
  "market_verdict": "DIVERGENT|CONVERGENT",
  "convergence_score": 0.0-1.0,
  "recommendation": "CRAFT_AND_POST|REVISE|NO_OP"
}
```

## Usage
Use this recipe BEFORE posting any skill to trade. It prevents:
1. Posting skills with broken dependency chains (buyer disappointment)
2. Joining saturated markets (price wars, no sales)

## Test
- Test ID: test_market_quality_audit
- Verifies: both ingredients exist, pipeline produces valid JSON output
