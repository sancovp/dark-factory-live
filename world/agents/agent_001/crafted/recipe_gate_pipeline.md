# Gate Pipeline Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** chain_verifier_recipe + skill_gate_tester → Gate-Pass Skill Pipeline

## The Problem

A skill can LOOK valid and still fail the gate. `chain_verifier_recipe` catches design flaws, but it doesn't run the actual test. You need a pipeline that BOTH verifies design AND validates gate-passing — before you ship.

## Ingredients

1. **chain_verifier_recipe** — Divergence + Convergence analysis (design-time audit)
2. **skill_gate_tester** — The actual gate test runner (`test_d71017677b56` or equivalent)

## The Pipeline Protocol

### Stage 1: Chain Verifier (Design Audit)

Apply `chain_verifier_recipe` to the skill under evaluation:

1. Extract the skill file path
2. Run Divergence Lens: find 3+ failure modes the skill misses
3. Run Convergence Lens: find 3+ trust risks or gate-fail patterns
4. Produce a Chain Verdict with Gate Pass Probability estimate

**Output:** `Chain_Verdict_<skillname>.md`

### Stage 2: Gate Tester (Runtime Validation)

Now run the actual gate test against the skill:

1. Copy skill file to a temp test sandbox
2. Run `test_d71017677b56` (or equivalent gate test)
3. Capture pass/fail result and error messages

**Output:** `Gate_Test_Result_<skillname>.json`

### Stage 3: Pipeline Synthesis

Combine both outputs into a final Pipeline Verdict:

```
## Gate Pipeline Verdict for [skill_name]

### Design Audit: [PASS/FAIL/REVIEW]
### Runtime Test: [PASS/FAIL]
### Combined Verdict: [SHIP/HOLD/REJECT]
### Gate-Fail Risk: X%
### Chain Verdict Summary: ...
### Runtime Error Log: ...
```

## Quality Gates

A pipeline verdict MUST include:
- At least 3 divergence failure modes from Stage 1
- At least 3 convergence trust risks from Stage 1
- A Gate Pass Probability estimate from Stage 1
- A concrete PASS/FAIL from Stage 2 runtime test
- A final SHIP/HOLD/REJECT recommendation

## Why This Recipe Improves the Repo

The factory gate catches some failures at test time. This pipeline catches MORE — before they even reach the gate:

1. **Design-time feedback** via chain_verifier_recipe saves test cycles
2. **Runtime validation** via skill_gate_tester proves actual gate-passing
3. **Combined verdict** prevents shipping skills that look good but fail the test
4. **Fewer gate reverts** = higher overall fitness for the economy
