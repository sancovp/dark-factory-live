# Skill Gap Finder Recipe

**Type:** Recipe
**Rarity:** Epic
**Composes:** Convergence Lens + Divergence Validator Lens + Dependency Lens → Skill Opportunity Report

## The Problem

Throughput is low (9 skills across all agents). The reason: agents don't know *what to craft* that will be valuable and undersupplied. They guess, or copy others, or pick the highest-paying quest without checking if the output already saturates the market. The result: convergent craft patterns, oversupplied skills, and missed opportunities.

This recipe changes that. It maps the game state — quest board, trade board, agent stats — and identifies where the gaps are: skill types in low supply, demand patterns nobody serves, and high-value quests nobody's taking.

## Ingredients Required

1. **Convergence Lens** (`crafted/convergence_lens.md`) — finds what everyone is doing, flags oversupply
2. **Divergence Validator Lens** (`crafted/divergence_validator_lens.md`) — recommends the underserved counter-move
3. **Dependency Lens** (`crafted/dependency_lens.md`) — traces demand→supply chains to find root-cause gaps

## The Pipeline

### Stage 1: Convergence Scan

Apply **Convergence Lens** to the full game state JSON (`../../game.json`):

- Scan `trade_board` for listed skills by type (Template/Lens/Prosthesis/Recipe/etc.)
- Count skill types in trade listings → identify oversaturated types
- Scan `quest_log` for accepted quests → identify overworked paths
- Scan `agents` stats for symmetric behavior (same craft/quest ratios)
- Output: `{oversupplied_types: [...], overworked_quests: [...], symmetric_agents: [...]}`

### Stage 2: Gap Identification

Apply **Divergence Validator Lens** to Stage 1 output:

- For each oversupplied type, compute the divergent skill TYPE that would NOT be redundant
- For each overworked quest, compute the adjacent quest type nobody is taking
- Score each potential gap by: `opportunity_score = demand_proxy / supply_proxy`
- Filter to gaps with score > 2.0 (genuine undersupply)
- Output: `{gaps: [{type, description, score, rarity_estimate, ingredients_needed}]}`

### Stage 3: Dependency Trace

Apply **Dependency Lens** to Stage 2 gap list:

- For each gap, trace what *other* skills it depends on (what would an agent need to buy to fill this gap?)
- Identify "anchor skills" — high-value components that multiple gap-filling skills would require
- Compute the supply chain potential: how many downstream recipes would this gap enable?
- Output: `{anchor_skills: [...], supply_chain_potential: {...}}`

### Stage 4: Synthesize Report

Combine all three stages into a final **Skill Opportunity Report**:

```markdown
# Skill Gap Report — [timestamp]

## Oversupplied Areas
- [type]: [count] existing skills, [recommendation to avoid]

## Identified Gaps (ranked by opportunity score)
1. **[Gap Name]** (score: X.X)
   - Skill Type: [type]
   - Rarity Estimate: [common/uncommon/rare/epic]
   - Why it fits: [specific reasoning]
   - Ingredients needed: [typed list]
   - Anchor skill leverage: [how many downstream recipes this enables]

## Top Recommendation
Craft **[TOP GAP]** using [specific ingredients]. Estimated output rarity: [X].
Supply chain value: [description of what this enables].
```

## Quality Gates

A valid Skill Gap Report must include:
- At least 2 oversupplied areas (what to avoid)
- At least 3 identified gaps with opportunity scores
- At least 1 gap with score > 3.0 (high-confidence opportunity)
- Dependency trace for the top gap (what components it needs)
- A specific, actionable recommendation (not just "craft more skills")

## Why This Is Epic

This recipe creates **market infrastructure**:
1. Agents using it make smarter craft decisions → throughput increases
2. Gaps it identifies create demand for typed components → new supply chains form
3. It composes THREE lenses in sequence — rare, multi-step composition
4. Its output is itself a tradeable artifact (the Opportunity Report)
5. It's reusable every round as the economy evolves

## Meta-PE Reflection

This recipe is itself a meta-level tool — it doesn't craft a skill, it tells you what skill to craft. That's the highest leverage possible: a recipe that generates more recipes. The standing deity rule (convergence is punished, divergence rewarded) is its core operating principle — the Convergence Lens finds the convergence to punish; the Divergence Validator prescribes the reward.
