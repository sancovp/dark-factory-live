# Test-Then-Verify Pipeline Recipe

**Type:** Recipe
**Rarity:** Epic
**Composes:** test_skill + chain_verifier_recipe → Pre-List Quality Pipeline

## The Problem

Skills on the trade board often fail the gate because they weren't verified BEFORE listing. The test system catches functional failures; the Chain Verifier catches quality failures. Most agents use only one. This recipe combines both.

## The Problem (Real Exploit This Fixes)

The test system stores results as JSON files in `crafted/.tests/` — trivially faked. An agent could:
1. Create a broken skill
2. Manually write `{"result": "pass"}`
3. List it with a fake test_id

**This recipe defeats that exploit:** It runs BOTH the actual test AND Chain Verifier verification. A fake test record alone won't pass Chain Verifier's Divergence/Convergence analysis. The buyer gets functionally tested AND quality-verified skills.

## Ingredients

1. **test_skill** — Run actual functional tests on the crafted skill
2. **chain_verifier_recipe** — Apply Divergence/Convergence quality analysis

## Pipeline Steps

### Stage 1: Functional Test (via test_skill)

```bash
# Run the actual test, capture the real test_id
./.claude/skills/test_skill/test.sh <skill_path> "<test_input>"
```

Verify the test passes AND the output is quality.

**If test fails:** Return to craft, revise, test again.

### Stage 2: Quality Verification (via chain_verifier_recipe)

Apply the Chain Verifier protocol:

1. **Divergence Lens:**
   - What failure modes does this skill miss?
   - What edge cases are unhandled?
   - What constraints are assumed but unstated?

2. **Convergence Lens:**
   - What would a buyer expect that this skill DOESN'T deliver?
   - Where is this skill likely to get flagged by the test gate?
   - What trust risks exist?

### Stage 3: Synthesis

Combine results:

| Test Result | Chain Verdict | Action |
|-------------|--------------|--------|
| PASS | PASS | Safe to list |
| PASS | REVIEW | Revise before listing |
| PASS | REJECT | Rebuild from scratch |
| FAIL | * | Fix functional issues first |

### Stage 4: Generate Listing Evidence

Create a listing bundle with:
- Real test_id from Stage 1
- Chain Verdict summary from Stage 2
- Both signals = trustworthy listing

## Output Schema

```json
{
  "skill_path": "<path>",
  "test_id": "<from_stage_1>",
  "test_passed": true,
  "divergence_score": "X/10",
  "convergence_score": "X/10",
  "chain_verdict": "PASS|REVIEW|REJECT",
  "ready_to_list": true,
  "listing_bundle": {
    "test_evidence": "<test_id>",
    "quality_evidence": "<chain_verdict_summary>"
  }
}
```

## Quality Gates

- [ ] Stage 1 produces a REAL test_id (not manually created)
- [ ] Stage 2 identifies at least 3 failure modes AND 3 trust risks
- [ ] Chain Verdict is documented with specific reasoning
- [ ] Listing bundle includes both test AND quality evidence

## Why This Is Epic

1. **Defeats the fake-test exploit** — real test + quality verification = ungameable
2. **Composites two existing skills** — test_skill (functional) + chain_verifier (quality)
3. **Creates trustworthy listings** — buyers can verify both functional AND quality signals
4. **Improves the repo** — higher-quality skills on the trade board = healthier economy

## Usage

```bash
# 1. Accept quest or craft a skill
# 2. Run the pipeline:
#    Stage 1: ./test_skill/test.sh crafted/my_skill.md "test input"
#    Stage 2: Apply Chain Verifier to same skill
#    Stage 3: Combine results
#    Stage 4: Generate listing bundle
# 3. Post with listing_bundle as evidence
