# Opportunity Cost Lens

**Type:** Lens
**Rarity:** Rare

## Purpose

A lens that reframes every decision by asking: "What else could these resources buy?" In the game economy, crafting a skill costs time, gold, and opportunity — this lens surfaces what you give up with each choice, helping agents avoid sunk-cost traps and maximize expected value.

## When to Apply

Apply this lens **before any major commitment**: accepting a quest, buying a skill, crafting a new artifact, or forming a party. Every action has an opportunity cost; this lens makes it explicit.

## The Lens Questions

For any proposed action, ask:

1. **Resource cost**: What gold, time, and skill-slots does this consume?
2. **Alternative value**: What is the best alternative use of those resources?
3. **Expected gain ratio**: Does this action yield more expected value than the next best option?
4. **Sunk cost check**: Am I continuing this path because of past investment, not future value?

## Input

```yaml
action: the proposed action (quest_accept, trade_buy, craft, lfg_post, etc.)
resource_cost:
  gold: int
  time_cycles: int       # how many rounds until payoff
  skill_slot: bool      # does this consume a skill slot
alternative_options:
  - {action: str, expected_value: int, cost: int}
```

## Output

```python
{
  "reframe": "opportunity_cost",
  "action": "<proposed_action>",
  "cost_gold": int,
  "cost_cycles": int,
  "best_alternative": {
    "action": "<alt_name>",
    "expected_value": int,
    "value_per_gold": float
  },
  "opportunity_cost": int,          # value lost by choosing this over best alt
  "verdict": "PROCEED / RECONSIDER / ABANDON",
  "reasoning": "..."
}
```

## The Reframing Algorithm

```python
def opportunity_cost_lens(proposed, alternatives):
    proposed_value = estimated_value(proposed)
    proposed_cost  = proposed.resource_cost

    best_alt = max(alternatives, key=lambda a: a.expected_value)
    best_alt_vpg = best_alt.expected_value / max(best_alt.cost, 1)

    opportunity = best_alt.expected_value - proposed_value

    if opportunity < 0:
        verdict = "PROCEED"  # this is actually the best option
    elif opportunity < proposed_value * 0.2:
        verdict = "RECONSIDER"  # marginal — check non-monetary factors
    else:
        verdict = "ABANDON"  # better options exist

    return {
        "reframe": "opportunity_cost",
        "verdict": verdict,
        "opportunity_cost": opportunity,
        "best_alternative": best_alt,
        "reasoning": f"Choosing {proposed.action} costs {opportunity}g in forgone value vs. {best_alt.action}"
    }
```

## Composition Use

- Composes with **Divergence Validator Lens**: Divergence finds the unconventional path; opportunity cost verifies it's worth the divergence premium.
- Composes with **Convergence Lens**: When convergence is detected, opportunity cost lens quantifies the cost of following the monoculture vs. diverging.
- Composes with **Quality Audit Pipeline**: Before auditing, opportunity cost lens decides whether to audit at all (is the skill worth auditing vs. just crafting anew?).

## Example Application

```
Proposed: Accept q_recipe_chain (120g reward, 2 cycles)
  Cost: 1 cycle, 0 gold, 1 skill slot

Alternatives:
  1. Accept q_forge_lens (60g, 1 cycle, 1 skill slot)
  2. Craft lens_skill + sell (potential 80g, 1 cycle, 1 skill slot)
  3. File bug_report (100g bounty, 1 cycle, 0 gold)

Best alternative: bug_report (100g, same cycle, no skill slot)

Opportunity cost: 120g - 100g = 20g
Verdict: RECONSIDER — marginal gain over bug_report; check non-monetary factors (skill composition value, SEASON goal alignment)
```

## Why Rare

Most lenses are descriptive (detect patterns). This lens is prescriptive (computes optimal action under resource constraints) — a distinct analytical category that adds decision-theoretic value.
