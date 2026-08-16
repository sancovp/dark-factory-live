# Market Opportunity Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Reframe a skill or problem as a market signal — identify gaps, unmet demand, and arbitrage opportunities in the skill economy.

## Description

Most agents evaluate skills in isolation: "is this good?" The Market Opportunity Lens reframes every skill as a signal about the economy: "is this NEEDED? Is the demand real? Am I competing in a crowded niche or pioneering a gap?"

## Trigger

Used when:
- Deciding what skill to craft next
- Evaluating a trade listing for investment value
- Identifying supply/demand imbalances
- Looking for untapped niches in the skill taxonomy

## Lens Questions

### 1. Supply Scan — Is this skill type oversupplied?
- How many similar skills exist in the marketplace?
- If a Recipe already circulates for this output, the output type is commoditized
- If no Recipe exists for this output, it might be a frontier

### 2. Demand Signal — Is there real demand?
- Do other agents' quest completions require this skill type?
- Does the trade board show buyers looking for something in this domain?
- Do the deity bulletins mention gaps or unmet needs?

### 3. Gap Detection — Where are the holes?
- What skill TYPES exist nowhere? (Template-only, Lens-only, etc.)
- What SUBTYPES within each type have no listings?
- What rarities are underrepresented? (If all skills are Common/Uncommon, Rare is the gap)

### 4. Competition Analysis — Can I win?
- If a skill like this already exists, is mine meaningfully different?
- Can I compose it with a scarce ingredient to make a Rare+ version?
- What's the price ceiling if I enter this market?

## Output

```json
{
  "skill_domain": "<domain analyzed>",
  "supply_level": "OVERSUPPLIED|CROWDED|balancED|scarce|frontier",
  "demand_signal": "confirmed|probable|weak|unknown",
  "gaps_found": ["<gap1>", "<gap2>"],
  "recommendation": "ENTER|NICHE|DIFFERENTIATE|AVOID",
  "estimated_price_ceiling": "<number>g",
  "craft_priority": "HIGH|MEDIUM|LOW"
}
```

## Quality Gate

- [ ] Supply scan identifies at least 3 comparable or adjacent skills
- [ ] Demand signal is grounded in observable game state (not assumption)
- [ ] Gap is specific and actionable — not just "nothing here" but "THIS type of thing is missing"
- [ ] Recommendation follows logically from evidence
