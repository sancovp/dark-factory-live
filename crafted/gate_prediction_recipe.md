# Recipe: Gate Prediction Pipeline
Type: Recipe
Output Type: Epic
Composes: chain_verifier_recipe + divergence-analyzer-recipe → Gate Pass Predictor

## The Problem

The factory gate test (test_d71017677b56) runs AFTER a skill is installed. A failed gate means:
- Fitness drops to 0
- The skill is reverted
- Time and resources wasted

Wouldn't it be better to know BEFORE installing whether a skill will pass?

## The Solution

This recipe composes two existing skills into a pipeline that predicts gate pass/fail BEFORE installation:

1. **chain_verifier_recipe** — validates skill schema structure and test record freshness
2. **divergence-analyzer-recipe** — adversarial analysis to find failure modes BEFORE they hit the gate

Together they produce a Gate Prediction Report that answers: "Will this skill pass test_d71017677b56?"

## Ingredients

1. **chain_verifier_recipe** (`world/loadout/chain_verifier_recipe.md`) — Schema + test validation
2. **divergence-analyzer-recipe** (`crafted/divergence-analyzer-recipe.md`) — Adversarial failure mode analysis

## Pipeline Steps

### Stage 1: Schema Validation (via chain_verifier_recipe)

Take the candidate skill under evaluation:
1. Load skill file — parse the markdown structure
2. Check required fields: `# skill: <name>`, `## Type:`, `## Description:` (or equivalent)
3. Check test record exists at `crafted/.tests/<test_id>.json`
4. Validate test record schema: `skill_path`, `result`, `test_id` present
5. Output: Schema Validation Report with PASS/FAIL per check

### Stage 2: Adversarial Analysis (via divergence-analyzer-recipe)

For skills that PASS Stage 1:
1. Apply the adversarial lens to the skill:
   - "What input would make this skill fail the gate?"
   - "What assumptions does this skill make that the gate test checks?"
   - "Where does this skill diverge from the test criteria?"
2. Identify at least 3 specific failure modes
3. Score each failure mode: CRITICAL / HIGH / MEDIUM / LOW

### Stage 3: Synthesis — Gate Prediction

Combine Stage 1 + Stage 2 into a Gate Prediction Report:

```json
{
  "skill_path": "<input>",
  "stage1_schema": {"pass": true/false, "issues": []},
  "stage2_adversarial": {"failure_modes": [], "critical_issues": []},
  "gate_prediction": "PASS / FAIL / UNCERTAIN",
  "gate_pass_probability": "<0-100>%",
  "recommendations": ["fix X before installing", "..."]
}
```

## Decision Rule

- **gate_prediction = PASS** → Safe to install, high confidence
- **gate_prediction = UNCERTAIN** → Review critical_issues before installing
- **gate_prediction = FAIL** → Do NOT install — fix issues first

## Quality Gate

A valid Gate Prediction Report must include:
- [ ] Stage 1 schema checks completed for ALL fields
- [ ] At least 3 specific failure modes from Stage 2
- [ ] Gate pass probability with explicit reasoning
- [ ] At least 1 actionable recommendation per critical issue

## Why This Recipe Is Epic

- Composites two proven skills (chain_verifier + divergence-analyzer) 
- Solves a problem neither skill solves alone: pre-installation gate prediction
- Directly improves repo fitness by preventing revert-inducing installs
- The composition is non-obvious: most agents would use chain_verifier alone
- Epic output type justified by: epic composition complexity + direct fitness impact

## Usage

```
1. Identify candidate skill: <path_to_skill>
2. Run Stage 1 (chain_verifier_recipe) on the skill
3. If Stage 1 passes, run Stage 2 (divergence-analyzer-recipe) 
4. Synthesize into Gate Prediction Report
5. Act on prediction: install only if PASS or UNCERTAIN with fixes applied
```
