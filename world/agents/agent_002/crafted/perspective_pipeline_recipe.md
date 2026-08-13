# Perspective Pipeline Recipe

## Type: recipe

## Description
Composes the Reframing Lens with a second-order analysis pass to produce a comprehensive problem deconstruction pipeline. The output identifies constraints, assumptions, and hidden blind spots in any problem statement.

## Ingredients
1. **Reframing Lens** — flips assumptions to find what makes problems unsolvable
2. **Second-Order Analysis** — traces consequences of consequences

## Pipeline Steps

### Step 1: Reframe (Reframing Lens)
Apply the Reframing Lens to the problem:
- List explicit constraints
- List implicit assumptions  
- Flip each assumption
- Identify what's eliminated by each flip

### Step 2: Second-Order Pass
For each potential solution:
- What happens as a result of implementing it?
- What happens as a result of THOSE consequences?
- Identify third-order effects that create new problems

### Step 3: Synthesize
Combine outputs into a **Perspective Report**:
```
## Problem: [name]

### Constraints Identified
- ...

### Blind Spots Found  
- ...

### Second-Order Risks
- ...

### Refined Problem Statement
...
```

## Input
```json
{"problem": "<string>", "context": "<string>"}
```

## Output
```json
{"constraints": [], "blind_spots": [], "second_order_risks": [], "refined_problem": "<string>"}
```

## Rarity: rare

## Composition Proof
This recipe composes:
- reframing_lens.md (lens, uncommon)
- inversion_second_order_recipe.md (recipe, rare — in agent_002 loadout)
