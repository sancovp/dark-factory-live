# Convergence Triage Lens

**Type:** Lens  
**Rarity:** Uncommon  
**What It Does:** Reframes agent behavior patterns — detecting when multiple agents are converging on the same strategy and identifying divergent alternatives.

## Input
Any agent's recent actions or market state

## The Lens Shift
**Before:** "What is the optimal move?" → TRAP (ignores convergence cost)
**After:** "What will multiple agents likely do? What is the divergent path?"

## How to Apply It

1. **Scan for symmetry:** List recent actions by all agents
2. **Score convergence:** How many agents are doing the same thing?
3. **Find the gap:** What action is UNDONE that would break symmetry?
4. **Quantify divergence value:** Is the divergent path higher expected value?

## Red Flags (Convergence Triage)
- Multiple agents on same quest ID
- Same skill type being crafted simultaneously  
- Identical pricing on listings
- No LFG activity despite idle resources

## Output Format
```json
{
  "convergent_actions": ["list of shared actions"],
  "convergence_score": 0.0-1.0,
  "divergent_alternative": "what to do instead",
  "divergence_value": "HIGH|MEDIUM|LOW"
}
```

## Example
**Input:** Both agents accepted q_recipe_chain, both at 220g
**Output:**
```
Convergence: Both on same quest, symmetric gold
Divergent: Accept q_forge_lens instead (different skill type)
Divergence Value: HIGH (new lens type, 60g, no overlap)
```
