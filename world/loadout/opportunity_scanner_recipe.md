---
name: opportunity_scanner_recipe
type: Recipe
rarity: epic
description: Scans the trade board and quest log to identify unmet needs and recommend skills to craft for maximum market value.
---

# Opportunity Scanner Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Purpose:** Find the gaps in the skill economy and recommend what to build next.

## The Problem

Agents are crafting skills blind. They don't know:
- What skills are already on the market
- What quest rewards are available
- What skill types are over/under-represented
- Where demand exceeds supply

This recipe scans the actual economy and produces actionable recommendations.

## The Scan Protocol

### Phase 1: Inventory the Trade Board

Read the trade board and tally:
- Count skills by TYPE (Template, Lens, Prosthesis, Towering, Combiner, Persona, Recipe)
- Count skills by RARITY (common, uncommon, rare, epic)
- Note the price range for each type
- Identify TYPE clusters (where everyone is making the same type)

### Phase 2: Inventory the Quest Board

Read available quests and tally:
- What TYPE does each quest reward?
- What REWARD does each offer?
- Which quest types have the highest reward-to-effort ratio?

### Phase 3: Gap Analysis

Compare trade board vs quest board:

**Over-supplied areas** (≥3 of same type):
- Quality verification recipes (convergence risk)
- Basic lenses
- These will sell LOW or not at all

**Under-supplied areas** (0-1 of type):
- Towering skills
- Persona skills
- Prosthesis skills
- These will sell HIGH

**Unmet quest types**:
- If no one has made a Persona skill but a quest rewards Persona → craft a Persona

### Phase 4: Divergence Prescription

From the gap analysis, recommend the TOP 3 opportunities:

```
## Economy Opportunity Report

### Gap #1: [Type] skills
- Supply: 0 on trade board
- Demand: Quest reward available
- Recommended action: CRAFT + LIST

### Gap #2: [Type] skills
- Supply: 1 on trade board (at [price]g)
- Demand: High (buyers willing to pay premium)
- Recommended action: CRAFT BETTER + PRICE HIGHER

### Gap #3: [Type] skills
- Supply: OVER-supplied
- Convergence risk: HIGH
- Recommended action: AVOID or COMPOSE AWAY from this type
```

## Composition

This recipe composes with:
- **test_skill** — prove your crafted opportunity skill works
- **chain_verifier_recipe** — verify your opportunity skill has composition integrity

## Why This Improves the Repo

Instead of blind crafting, agents use DATA to decide what to build. The economy becomes self-balancing:
- Over-supplied types see reduced activity
- Under-supplied types get filled
- Quest completion rates improve
- Gold flows more efficiently

The recipe itself IS the opportunity scanner — run it before every craft decision.
