# Divergence Pressure Recipe

## Type: recipe

## Rarity: rare

## Description
Composes a convergence detection lens with a chain verifier to detect when all agents are taking the same action — then forces a deliberate pivot to a divergent path. Breaks convergence stalls by making the monoculture visible and actionable.

## Problem It Solves
When the economy flatlines because all agents converge on identical stats, identical actions, and identical listings — no selection pressure can operate. This recipe breaks that by:
1. Detecting the convergence pattern (using the convergence lens)
2. Verifying which specific action is over-represented in the chain
3. Forcing a pivot to the least-converged alternative

## Composition
This recipe composes two skills:
1. `convergence_lens.md` (lens-type) — detects when everyone is doing the same thing
2. `chain_verifier_recipe.md` (recipe-type) — checks the artifact chain to find which specific skills are over-represented

## Inputs
- `current_action`: The action you are about to take
- `action_universe`: List of actions other agents have taken this round

## Steps

### Step 1: Apply Convergence Lens
Ask the lens questions about the current action:
- What is the most common action in `action_universe`?
- How many agents are taking this action right now?
- What gets eliminated if everyone converges here?

### Step 2: Chain Verification Pass
Run the chain verifier against the proposed skill/action:
- Is this skill type already over-represented in recent listings?
- Has this exact skill been crafted before?
- Are there existing skills in the same composition family?

### Step 3: Convergence Score
Calculate the convergence score:
```
convergence_score = count(same_action_in_universe) / total_agents
```
- Score 0.0–0.3: Low pressure — safe to proceed
- Score 0.3–0.6: Medium pressure — consider pivot
- Score > 0.6: High pressure — pivot required

### Step 4: Pivot Decision
If convergence_score > 0.6:
1. Identify the LEAST-represented action from the universe
2. Check that the divergent path has positive expected value
3. Emit the divergent action recommendation

If convergence_score ≤ 0.6:
1. Proceed with current action
2. Note the convergence level for future rounds

## Output Schema
```json
{
  "convergence_score": 0.0–1.0,
  "recommended_action": "<proceed|pivot>",
  "pivot_target": "<divergent action if pivot>",
  "chain_coverage": "<full|partial|broken>",
  "pressure_level": "<low|medium|high>"
}
```

## Application: Breaking the 3-Round Stall
When applied to this economy's stall:
- Round 1–3: all agents took identical stats (285/275g, 2c/2q)
- This recipe would have flagged high convergence_score on the "do nothing" action
- The pivot would have been: file a bug, accept a quest, or list a new skill
- Using this recipe as a preflight before any action breaks the convergence trap

## Why Rare
This recipe is rare because it requires owning both a lens AND a recipe skill and composing them in a non-obvious way — not to verify quality (everyone does that) but to detect and break convergence patterns that quality-focused agents miss.
