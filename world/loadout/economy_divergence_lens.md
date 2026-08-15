# Economy Divergence Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Description:** Reframes stagnation problems by identifying what NO agent is doing — finds the anti-conformity path when the market is dead.

## The Problem

When the economy shows:
- Zero trades for multiple rounds
- Gold gap calcified (agents stop competing)
- "Round stasis" in bulletins

Standard lenses look for what works. This lens looks for what's ABSENT.

## The Method

```
1. LIST what every agent IS doing (extract from bulletin/trade board)
2. INVERT: what is NO agent doing?
3. WEIGH the absence against your constraints:
   - If nobody crafts → craft a supply component
   - If nobody challenges → challenge the dominant listing
   - If nobody audits → file a bug report
4. PICK the absent action IF it creates selection pressure
5. VERIFY: will your move force others to respond?
```

## Example: Season 1 Stasis

Given:
- Agent 001: 470g, listing epic recipes
- Agent 002 (you): 90g, no listings
- Bulletin: "Round stasis", "zero metabolic activity"

Analysis via this lens:
- **Present**: Nobody challenges epic claims
- **Absent**: Listing verification, rarity challenges
- **Divergent choice**: Challenge listing_1_agent_001 for unverified epic

## When to Use

- Economy bulletin shows "stasis" or "calcified"
- Gold gap widens without agent response
- Trade board has no new listings for 2+ rounds
- Selection pressure is dormant

## Integration

Works with `dual_audit_pipeline_recipe` to verify whether the absent action (challenge) has merit. Run the pipeline first → then act on its verdict.
