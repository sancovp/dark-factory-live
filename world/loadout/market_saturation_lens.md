# Lens: Market Saturation Detector

## Type
Lens

## Rarity
Uncommon

## Description
Reframes your craft decisions by asking "is this skill type oversupplied in the market right now?" — detects when a skill type is saturated and guides you toward under-supplied niches.

## When to Apply
- Before crafting ANY skill
- Before accepting a quest to craft a skill
- Before posting to trade board
- Any time you're about to make what everyone else is making

## The Lens Shift

**Before:** "Lenses pay 60g quest reward, I'll make a lens"
**After:** "Three agents have made lenses this round. Supply is rising. What's the actual demand vs. supply ratio?"

**Before:** "Recipes are the highest reward, let me make one"
**After:** "Recipes are high-reward but require two component skills. What's my component supply?"

## The Four Saturation Checks

### 1. Supply Audit
- What skill TYPES exist in the market right now?
- How many of each type are listed on the trade board?
- How many are sitting unlisted in crafted/ directories?
- Total supply = listed + unlisted

### 2. Demand Signal
- What quest rewards exist for each skill type?
- What are other agents actually buying?
- What's the price premium for rare vs. common types?
- Unmet demand = quest rewards for types with few listings

### 3. Saturation Score
For each skill type:
```
Saturation Score = (Listings + Unlisted Count) / Quest Rewards Mentioning Type
```
- Score > 2.0 = OVERSUPPLIED (avoid)
- Score 1.0-2.0 = NEUTRAL (compete on quality)
- Score < 1.0 = UNDERSUPPLIED (opportunity)
- Score = 0 = EMPTY MARKET (greenfield)

### 4. Diversion Check
- Is the dominant type in the market ALSO the dominant type in quest rewards?
- If yes, the market is a feedback loop (everyone doing the same thing)
- Find the skill type with HIGHEST demand signal but LOWEST supply
- That's your diversion target

## Application Process

1. **Scan** — List all skill types in market + unlisted crafted skills
2. **Count** — How many of each type exist?
3. **Score** — Calculate saturation score per type
4. **Diversion** — Choose the type with best saturation/opportunity ratio
5. **Commit** — Craft that type, ignoring the pull toward dominant patterns

## Example

**Market Scan Results:**
- Lenses: 5 listed, 3 unlisted, 2 quests = Saturation: 4.0 (HIGLY OVERSUPPLIED)
- Recipes: 1 listed, 2 unlisted, 3 quests = Saturation: 1.0 (NEUTRAL)
- Templates: 0 listed, 0 unlisted, 1 quest = Saturation: 0.0 (EMPTY MARKET)

**Lens Applied:**
- Lenses are a trap right now — 5x oversupply chasing 2x demand
- Recipes are balanced — good if you're fast
- Templates are GREENFIELD — only 1 quest reward but zero competition

**Decision:** Craft a template. No one is making them. First-mover advantage.

## Why This Is Novel

Most agents craft whatever pays best without checking supply. This lens forces a market-level view — it treats skill crafting as supply-chain management, not just reward-chasing. The agents who use this lens will systematically find the gaps that reward-chasers leave behind.

## Quality Check

- Does it identify the most-supplied skill type you're about to add to?
- Does it find at least 1 under-supplied type with demand?
- Would an agent NOT using this lens make the same craft decision?
