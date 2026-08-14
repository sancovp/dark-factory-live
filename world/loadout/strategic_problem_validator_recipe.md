# Recipe: Strategic Problem Validator

**Type:** Recipe  
**Rarity:** Rare  
**Composes:** Blank Slate Lens + Gate Probability Estimator → Verified Problem Statement with Implementation Plan

## Purpose

Before committing resources to any problem, verify TWO things:
1. The problem is worth solving (Blank Slate Lens)
2. The solution will pass the gate (Gate Probability Estimator)

This recipe prevents wasted cycles on problems that shouldn't exist and solutions that won't ship.

## Ingredients Required

1. **Blank Slate Lens** (`crafted/blank_slate_lens.md`) — Verify the problem deserves solving
2. **Gate Probability Estimator** (`crafted/gate_probability_recipe.md`) — Verify the solution will pass

## Pipeline Steps

### Stage 1: Problem Verification (Blank Slate Lens)

Apply the Blank Slate Lens to your problem P:
1. Describe the world without P
2. Trace who built around P
3. Identify what solving breaks
4. Render a verdict: WORTH_IT / CONTEXT_NEEDED / NOT_WORTH_IT

**If verdict is NOT_WORTH_IT: STOP. Do not proceed.**

### Stage 2: Solution Verification (Gate Probability Estimator)

For each candidate solution:
1. Apply adversarial analysis (what can break?)
2. Check gate criteria (composition, no placeholders, correct type, testable)
3. Calculate gate pass probability

**If probability < 60%: STOP. Refine the solution or choose another.**

### Stage 3: Synthesis

Combine Stage 1 and 2 into a **Strategic Recommendation**:

```json
{
  "problem_verdict": "WORTH_IT",
  "problem_rationale": "...",
  "solution_candidates": [
    {"solution": "...", "probability": "75%", "verdict": "PROCEED"},
    {"solution": "...", "probability": "45%", "verdict": "REFINE or ABANDON"}
  ],
  "final_recommendation": "Proceed with candidate 1 using refinement to reach 80%+"
}
```

## Quality Gate

- [ ] Stage 1 produces a named verdict (not "maybe")
- [ ] Stage 2 produces probabilities for at least 2 candidate solutions
- [ ] Stage 3 links problem worth to solution probability
- [ ] If problem is NOT_WORTH_IT, recipe stops and documents why

## Why This Is Rare

Most agents jump straight to solving without verification. This recipe:
- Adds a problem-validation layer before solution-design
- Composes two meta-skills (lens + recipe) into a pipeline
- Prevents wasted effort on problems or solutions that won't pass
- Creates a reusable "verify before build" workflow

## Usage

```
1. Read crafted/blank_slate_lens.md
2. Apply Stage 1 to your problem
3. If WORTH_IT: proceed to Stage 2
4. Read crafted/gate_probability_recipe.md  
5. Apply Stage 2 to candidate solutions
6. Synthesize in Stage 3
7. Either proceed with confidence or stop early
```
