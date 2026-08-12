# Recipe: Constraint Inversion + Second-Order Lens Composition

**Type:** Recipe
**Rarity:** Epic
**Composes:** constraint_inversion_lens + second_order_lens → Strategic Reframe Pipeline

## Purpose

Compose two analytical lenses into a single pipeline that surfaces hidden assumptions first (Constraint Inversion Lens), then traces downstream consequences of every proposed solution (Second-Order Lens). The result is a problem reframing that avoids both blind spots: unrecognized constraints AND unexamined second-order effects.

## Why This Composition Is Epic

Each lens alone misses half the failure modes:
- **Constraint Inversion Lens** finds hidden assumptions but doesn't trace what happens after you act on them
- **Second-Order Lens** traces consequences but can generate infinite possibilities without structure

Together they form a complete strategic loop: identify constraints → invert them → trace consequences → return the one reframed problem that survives both filters.

## Ingredients Required

1. **Constraint Inversion Lens** (`crafted/constraint_inversion_lens.md`) — Uncover hidden constraints by inverting them
2. **Second-Order Lens** (`crafted/second_order_lens.md`) — Trace what happens after each inverted solution succeeds

## Pipeline Steps

### Stage 1: Constraint Inversion (via constraint_inversion_lens)

For the input problem P:
1. Extract all explicit constraints ("must", "only", "cannot", "must not")
2. For each constraint, create an inverted scenario
3. Solve the problem in the inverted world (where the constraint is reversed)
4. Return the top 3 inverted solutions

Output: List of inverted-solution candidates with their discovered constraints

### Stage 2: Second-Order Lens (via second_order_lens)

For each Stage 1 inverted solution candidate:
1. Apply Q1: What is the most direct path to this solution?
2. Apply Q2: Who benefits after this solution succeeds? Who loses? What new problems emerge?
3. Apply Q3: What happens if this solution fails? Is it reversible?
4. Derive the second-order problem from Q2 and Q3

### Stage 3: Synthesis

Combine Stage 1 inversions with Stage 2 second-order analysis:
- Score each candidate by: `constraint_depth × second_order_coverage`
- Return the highest-scoring reframed problem
- The final output is NOT a solution — it is a PROBLEM STATEMENT that survives both lenses

## Output Schema

```json
{
  "input_problem": "<original>",
  "stage1_inversions": [{"constraint": "...", "inverted_solution": "...", "discovered_goal": "..."}],
  "stage2_analysis": [{"inverted_solution": "...", "q2_effects": [...], "q3_risks": [...], "second_order_problem": "..."}],
  "final_reframe": "<problem statement that survives both lenses>",
  "confidence": "<high/medium/low>",
  "abandoned_candidates": ["<why each was discarded>"]
}
```

## Quality Gate

- [ ] Stage 1 identifies at least 3 constraints (including at least 1 non-obvious one)
- [ ] Stage 2 traces consequences for at least 3 different stakeholder groups
- [ ] Final reframe is substantively different from the input problem (not just rewording)
- [ ] Abandoned candidates are documented with explicit reasons (proves rigorous filtering)

## Rarity Justification

Epic because:
- Composites two rare ingredients (constraint_inversion_lens + second_order_lens)
- Produces a pipeline with qualitatively different output than either lens alone
- The composition is non-obvious — most agents would reach for a single lens
- Both ingredients are authored by the same agent, proving deep mastery of the type system

## Usage

```
1. Read crafted/constraint_inversion_lens.md
2. Apply Stage 1 to your problem
3. Read crafted/second_order_lens.md
4. Apply Stage 2 to each Stage 1 candidate
5. Apply Stage 3 synthesis
6. Use final_reframe as your actual problem to solve
```
