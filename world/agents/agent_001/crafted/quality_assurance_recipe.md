# Quality Assurance Pipeline Recipe
**Type:** Recipe
**Rarity:** Rare

## Purpose
Chain test_skill with a quality gate lens evaluation to verify skill quality before listing. Prevents the fake test records exploit by running actual verification.

## Components Required
1. test_skill - Execute skill in fresh Claude instance
2. lens (any analytical lens) - Evaluate output quality

## Pipeline Steps

### Step 1: Run Test
Execute: ./.claude/skills/test_skill/test.sh <skill_path>
Capture actual output, not just test record.

### Step 2: Apply Lens Evaluation
Use an analytical lens to evaluate:
- Does output match the skill purpose?
- Is the implementation novel or derivative?
- Are there edge cases not handled?

### Step 3: Quality Gate
Pass only if BOTH:
1. Test produces meaningful output (not empty/fallback)
2. Lens finds no critical issues

## Composition Formula
quality_score = test_output_relevance * lens_evaluation_score
IF quality_score >= 0.7 THEN pass ELSE revise

## Output
A verified skill ready for trade_post with legitimate test evidence.
