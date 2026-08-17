# Dependency Market Pipeline Recipe

**Type:** Recipe (Pipeline subtype)  
**Rarity:** Rare  
**Composes:** `dependency_trace_lens` + `market_diversity_lens` → Market-Opportunity Mapper

## Description

Maps the dependency graph of the skill economy and cross-references it against the trade board to identify orphaned skills (skills with unmet dependencies) and market gaps (missing skills that would complete high-value chains). The output is a ranked list of craft opportunities with market timing signals.

## Why This Improves the Economy

Most agents craft skills in isolation — they don't know what their skill would COMPLETE in someone else's pipeline. This recipe fixes that by tracing the dependency graph forward to find skills that need ingredients AND backward to find skills waiting to be assembled.

## Ingredients

1. **Dependency Trace Lens** (`dependency_trace_lens`) — maps backward + forward dependencies for any skill
2. **Market Diversity Lens** (`market_diversity_lens`) — identifies what's MISSING from the trade board

## The Pipeline

### Stage 1: Dependency Graph Walk

For each skill in the economy (loadout + trade board):

```json
{"skill_path": "<skill>", "mode": "both"}
```

Apply `dependency_trace_lens`:
- **Backward deps:** what does this skill require? (imports, references)
- **Forward deps:** what downstream skills need this?
- **Hub score:** how many skills depend on this one?
- **Orphaned:** true if forward_deps is empty AND backward_deps contains MISSING items

Output: `{skill, backward_deps, forward_deps, hub_score, orphaned}`

### Stage 2: Market Gap Scan

Apply `market_diversity_lens`:
```json
{"board_snapshot": "<trade_board + quest_board>"}
```

Cross-reference with Stage 1 output:
- Which backward deps are MISSING but appear in the market as wanted?
- Which orphaned skills have NO listings but are referenced by loadout skills?
- Which hub skills have NO trade listings (monopoly risk)?

Output: `{market_gaps: [{missing_skill, demand_score, opportunity_gold}]}`

### Stage 3: Opportunity Ranking

Combine dependency urgency × market demand:

```
opportunity_score = (backlog_urgency × hub_score) + (market_demand × price_equilibrium)
```

Rank top 5 opportunities and emit:
```
## Dependency Market Opportunity Report
=========================
Ranked Craft Opportunities:
  #1: <missing_skill> (hub_score: N, demand: HIGH, est. price: Ng)
  #2: <missing_skill> (hub_score: N, demand: MED, est. price: Ng)
  ...
  
Top Orphaned Skills (need ingredients):
  #1: <orphaned_skill> (blocked by: <missing_dep>)
  #2: <orphaned_skill> (blocked by: <missing_dep>)
  
Monopoly Alerts (hub skill with no listings):
  #1: <hub_skill> (N downstream deps, untraaded)
```

## Quality Gates

1. **Dependency trace must find at least 2 backward deps** OR identify ≥1 orphaned skill
2. **Market gap scan must identify at least 1 gap** not already on the trade board
3. **Opportunity score must differ meaningfully** from a random baseline (ranked, not uniform)

## Rarity Justification

Rare (Pipeline) because:
- Composes two Uncommon lenses into a novel capability neither provides alone
- Novel market-mapping function that addresses a real economy gap
- Creates a measurable improvement (ranked opportunities from graph theory)

## Example Application

Agent has `chain_verifier_recipe` but no lens to pair it with:
1. Run `dependency_trace_lens` on `chain_verifier_recipe` → backward_deps: [divergence_lens, convergence_lens], forward_deps: []
2. Run `market_diversity_lens` → missing_types: [lens]
3. Cross-reference: divergence_lens and convergence_lens are both MISSING from market AND needed as backward_deps
4. **Opportunity: craft divergence_lens or convergence_lens** → high hub_score × high demand = top-ranked craft opportunity

## Integration Points

- **Input:** game.json (for trade_board), .claude/skills/ (for loadout graph)
- **Output:** ranked craft opportunity list for agent decision-making
- **Downstream:** informs trade_safety_recipe's convergence analysis; prevents crafting dead-end skills
