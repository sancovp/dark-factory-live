# Divergence Inversion Pipeline

**Type:** Recipe
**Rarity:** Epic
**Composes:** Chain Verifier Recipe + Second-Order Inversion Lens → Failure-Mode Discovery Pipeline

## The Problem

Standard quality checks verify that skills pass the gate. But they miss the deeper question: *why might this skill fail in ways the gate doesn't catch?* This pipeline combines verification with second-order inversion to surface hidden failure modes.

## Ingredients

1. **Chain Verifier Recipe** — Applies Divergence + Convergence lenses to assess gate-pass probability.
2. **Second-Order Inversion Lens** — Examines what would causally produce failure, revealing failure modes missed by first-order analysis.

## The Pipeline Protocol

### Phase 1: Chain Verification (from Chain Verifier Recipe)
- Apply Divergence Lens: What obvious use case does this skill handle? What fails that most miss?
- Apply Convergence Lens: What dominant pattern does this skill follow? Where might the gate flag it?
- Record: Divergence Score, Convergence Score, Gate Pass Probability, Verdict

### Phase 2: Second-Order Inversion (from Second-Order Inversion Lens)
- State the desired outcome from Phase 1 (e.g., "The skill passes the gate")
- Invert completely (e.g., "The skill fails the gate")
- Ask second-order why: What causally produces that failure?
- Extract inverse requirements: What must not exist (for success) or must exist (for failure)?

### Phase 3: Synthesize
- Cross-reference Phase 1 and Phase 2 findings
- Identify failure modes NOT caught by the gate
- Produce actionable recommendations for strengthening the skill

## Output Format

```
Phase 1 Verdict: [PASS/REVIEW/REJECT]
Phase 2 Failure Modes: [list]
Phase 3 Recommendations:
  1. ...
  2. ...
  3. ...
Final Assessment: [SAFE/LIST-WITH-CAVEAT/DO-NOT-LIST]
```

## Why This Pipeline Works

By combining verification with second-order inversion:
1. Skills surface failure modes beyond gate-catchable defects
2. Buyers understand hidden risks before purchase
3. The skill economy improves through deeper quality signals

## Test Assertion

This pipeline produces output that includes all three phases with:
- A Phase 1 Verdict
- At least 2 Phase 2 Failure Modes
- At least 2 Phase 3 Recommendations
- A Final Assessment
