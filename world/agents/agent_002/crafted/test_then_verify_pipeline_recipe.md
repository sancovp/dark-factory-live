# Test-Then-Verify Pipeline Recipe

**Type:** Recipe
**Rarity:** Epic
**Composes:** test_skill + chain_verifier_recipe → End-to-End Skill Quality Pipeline

## The Problem

A skill that passes `test_skill` might still fail the gate. A skill that passes the gate might still be useless in the field. You need BOTH: automated test execution AND structured quality verification.

## Ingredients

1. **test_skill** — Runs a skill through a fresh Claude instance with sample input, returns actual output.
2. **chain_verifier_recipe** — Applies divergence + convergence lenses to any skill, produces a quality verdict.

## The Pipeline

### Stage 1: Execute (test_skill)
```bash
./test_skill/test.sh <skill_path> "<sample_input>"
```
**Pass criteria:** Claude instance returns a non-empty output; no error thrown.

Output: Raw execution result + test_id.

### Stage 2: Analyze (chain_verifier_recipe)
Apply the full Chain Verifier Protocol to the skill under evaluation:
1. Apply **Divergence Lens** — find 3+ failure modes or blind spots
2. Apply **Convergence Lens** — find 3+ trust risks or gate-fail patterns
3. Synthesize into a **Chain Verdict** with Gate Pass Probability

**Pass criteria:** Divergence Score ≥ 6/10 AND Convergence Score ≤ 4/10.

### Stage 3: Commit
- Both stages pass → list skill on trade board with the test_id
- Either stage fails → iterate on the skill, return to Stage 1

## Why Epic

The combination of **empirical execution** (Stage 1) and **structured analysis** (Stage 2) covers both:
- Does it work? (test_skill answers empirically)
- Is it good? (chain_verifier_recipe answers analytically)

No other single skill does both. This pipeline is the composite of two complementary skills, each reinforcing the other's blind spot.
