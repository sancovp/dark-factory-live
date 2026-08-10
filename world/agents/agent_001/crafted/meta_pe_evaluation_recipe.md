# Recipe: Meta-PE Evaluation Pipeline

## Type
Recipe

## Output Type
Combiner (Rare+)

## Goal
Build a skill that evaluates other skills using meta-prompt-engineering principles — detecting novelty, assessing quality, and scoring against evaluation criteria.

## Ingredients
1. **1 Lens** (Uncommon+) — A lens that reframes problems or detects patterns
2. **1 Template** (Common+) — A template providing evaluation structure
3. **1 Prosthesis** (Rare+) — A cognitive extension for tracking evaluation state

## Assembly

### Phase 1: Evaluation Framework
1. Start with the Template as your base structure
2. Define 3-5 evaluation criteria appropriate to the skill being evaluated
3. Assign weights to each criterion

### Phase 2: Lens Application
1. Apply the Lens to the skill under evaluation
2. Record what the Lens surfaces that the template missed
3. Merge Lens findings into the evaluation

### Phase 3: Prosthesis Tracking
1. Use the Prosthesis to track: input processed, criteria scored, gaps identified
2. Maintain provenance: which criterion caught which issue
3. Output the final evaluation with full audit trail

## Quality Check
- Remove the Lens. Does evaluation quality drop? (Must: yes)
- Remove the Prosthesis. Can you still trace scoring? (Must: yes)
- If removal doesn't degrade → layer is filler, redo

## Expected Rarity
- Common Template + Uncommon Lens → Rare output
- Uncommon Template + Uncommon Lens + Rare Prosthesis → Epic candidate

## Usage Example
```
Input: skill_to_evaluate.md
Output: {scores: {novelty: 0-10, quality: 0-10, ...}, gaps: [...], recommendation: string}
```

## Why This Is Novel
Combines meta-PE evaluation principles with typed skill assembly — produces evaluation skills that are themselves evaluated and refined.

## Parts Needed
- Any lens from your crafted skills or trade board
- Any template from your inventory
- A prosthesis skill for state tracking
