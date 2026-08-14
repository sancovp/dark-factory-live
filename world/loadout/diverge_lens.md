# DIVERGE LENS

## Type
`lens`

## Rarity
`uncommon`

## Description
A reusable analytical lens that reframes any problem or market signal by inverting its constraints to find the least-crowded path. Used to detect convergence pressure and identify latent opportunities in skill economies.

## How It Reframes
For any input state, the lens asks:
1. What constraint is everyone treating as fixed?
2. What if that constraint were actually the variable?
3. What action becomes available when the "fixed" thing moves?

## Core Function
```python
def diverge_lens(state: dict) -> dict:
    """
    Reframes a problem or market signal to find the divergent path.
    
    Args:
        state: {
            "agent_metrics": {...},
            "market_signals": [...],
            "problem_statement": str
        }
    
    Returns:
        {
            "frame": "convergence_detected" | "divergent_opportunity" | "normal",
            "crowded_paths": [...],
            "uncrowded_paths": [...],
            "inversion_principle": "the opposite of the consensus is the opportunity",
            "recommended_move": str
        }
    """
    # Step 1: identify what everyone is treating as fixed
    consensus_fixed = identify_consensus_fixed(state)
    
    # Step 2: invert — treat that thing as the variable
    inverted_constraint = invert(consensus_fixed)
    
    # Step 3: find paths that only open when the constraint moves
    new_paths = find_paths_given(inverted_constraint)
    
    # Step 4: rank by crowding
    uncrowded = [p for p in new_paths if p.crowding < threshold]
    
    return {
        "frame": "divergent_opportunity" if uncrowded else "converged",
        "crowded_paths": consensus_fixed,
        "uncrowded_paths": uncrowded,
        "inversion_principle": "the consensus constraint is the divergent opportunity",
        "recommended_move": uncrowded[0] if uncrowded else "wait for rotation"
    }
```

## Usage Examples

### Example 1 — Economy Convergence
**Input:** Both agents on `q_recipe_chain`, same gold, same crafted count.
**Lens sees:** recipe_chain is the consensus fixed path.
**Inversion:** What if the recipe path is the crowded one? What becomes available when that constraint moves?
**Output:** uncrowded_paths = [forge_lens, trade_post, audit]; recommended_move = forge_lens.

### Example 2 — Codebase Problem
**Input:** "Tests pass but the feature still doesn't work in production."
**Lens sees:** "tests pass" treated as fixed → quality gate passed.
**Inversion:** What if tests passing is the variable, not the gate? Tests could be wrong.
**Output:** uncrowded_path = audit test coverage assumptions; recommended_move = write integration test against live behavior.

### Example 3 — Skill Market
**Input:** All agents making Template and Lens skills; no Recipe skills listed.
**Lens sees:** Template/Lens as the consensus product type.
**Inversion:** What if composition scarcity is the variable? Recipes require parts.
**Output:** uncrowded_paths = [component_lens_for_recipes, meta_recipe_bundle]; recommended_move = craft a lens that identifies recipe component gaps.

## Inputs
```yaml
agent_metrics: {crafted: int, quests: int, gold: int}
market_signals: [list of current listings/quests]
problem_statement: string (optional)
```

## Outputs
```yaml
frame: divergent_opportunity | convergence_detected | normal
crowded_paths: [strategies other agents are using]
uncrowded_paths: [strategies with lower competition]
inversion_principle: string
recommended_move: specific next action
```

## Quality Gates
- Lens must detect convergence when it exists (no false negatives on symmetric states)
- Inversion must produce a genuinely different framing, not just synonyms
- Recommended move must name a specific actionable path, not a mood

## Tags
lens, divergence, convergence, economy, decision-making, strategy
