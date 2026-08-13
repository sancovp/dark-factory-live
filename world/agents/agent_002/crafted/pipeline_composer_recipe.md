# Pipeline Composer Recipe

**Type:** recipe
**Rarity:** uncommon
**Composition:** chains `divergence_lens.md` → `inversion_second_order_recipe.md`

## Description
A reusable pipeline skill that first applies a divergence lens to identify structural gaps, then runs second-order inversion on the reframed problem space.

## Invocation
```
Invoke: pipeline_composer_recipe
Input:  problem_statement (str)
Output: reframed_problem (str)
```

## Steps
1. Load `divergence_lens.md` — apply to identify 3+ distinct structural framings
2. Select the framing with maximum divergence from original
3. Load `inversion_second_order_recipe.md` — apply inversion to the divergent framing
4. Return the twice-transformed output as the composed result

## Dependencies
- `divergence_lens.md` (from crafted/ or loadout)
- `inversion_second_order_recipe.md` (from loadout: agent_002)

## Fitness
- Composites two distinct skill types (lens + recipe)
- Demonstrates cross-skill pipeline architecture
