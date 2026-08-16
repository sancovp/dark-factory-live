# Fitness Landscape Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Reframe decision problems as fitness landscapes — identifying peaks, valleys, and the ruggedness of the problem space

## The Concept
A "fitness landscape" maps solutions to their fitness (quality). Peaks = high-fitness solutions. Valleys = poor solutions. Ruggedness = deception (local peaks that mislead global search). This lens transforms any optimization problem into a topographic map.

## How to Use
When facing any decision, strategy, or skill selection problem:

1. **Map the terrain**: What are the "coordinates" (dimensions) of the problem space?
2. **Identify peaks**: What solutions have historically performed best?
3. **Detect valleys**: What choices lead to dead ends or fitness traps?
4. **Measure ruggedness**: Is the landscape smooth (predictable) or rugged (deceptive)?
5. **Find plateaus**: Where does effort not improve fitness (flat regions)?

## Application to World of Skillcraft

| Problem | Landscape Interpretation |
|---------|------------------------|
| Which skill to craft? | Peak = high-utility skill; valley = redundant/novelty-free skill |
| Accept quest or not? | Peak = high reward/path dependency; valley = opportunity cost trap |
| Trade or hold? | Peak = favorable price pressure; valley = overpay for inflated rarity |
| Loadout composition | Peak = proven dependencies; valley = circular deps / missing gates |

## Example: Skill Selection
- **Coordinates**: {skill_type, rarity, composition_count}
- **Fitness function**: quest_relevance × rarity_premium × novelty_bonus
- **Peak found**: "recipe" type, "rare" rarity, composes 2+ proven skills
- **Valley avoided**: "lens" type, "epic" rarity, self-referential

## Output Format
```
## Fitness Landscape Analysis

**Terrain**: [Smooth / Rugged / Chaotic]
**Peak locations**: [coordinate set of best solutions]
**Dangerous valleys**: [coordinate set to avoid]
**Recommended search strategy**: [Hill-climb / Random restart / Evolutionary]

**Key insight**: [One-sentence takeaway]
```

## When to Use
- Before accepting a quest: Map reward vs. skill development tradeoffs
- Before crafting: Verify you're climbing toward a peak, not a valley
- After a revert: Diagnose what local peak was misleading

## Rarity
uncommon — reframes optimization as spatial navigation

## Tags
optimization, decision-making, landscape, evolutionary, analysis
