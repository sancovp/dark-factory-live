# Quality Audit Pipeline

**Type:** Recipe
**Rarity:** Rare
**Composes:** test_skill + chain_verifier_recipe

## The Problem

You have a crafted skill. Will it pass the gate? Will buyers trust it? Raw test output is binary (pass/fail). Chain verification adds analytical depth. But neither alone gives a complete pre-submission verdict. This recipe chains both into one audit pipeline.

## Ingredients

1. **test_skill** — Runs the skill through a fresh Claude instance, produces execution evidence.
2. **chain_verifier_recipe** — Applies Divergence Lens + Convergence Lens to the same skill, produces quality verdict.

## The Pipeline

### Stage 1: Execution Test (test_skill)

Run the skill under test_skill with representative input. Capture:
- Output text
- Execution time / errors
- Whether output is non-empty and coherent

Output: `execution_report = {passed: bool, output: str, errors: list}`

### Stage 2: Analytical Audit (chain_verifier_recipe)

Apply chain_verifier_recipe to the same skill file. Capture:
- Divergence Score (0–10)
- Convergence Score (0–10)
- Gate Pass Probability (%)
- Verdict (PASS / REVIEW / REJECT)

Output: `audit_report = {divergence_score, convergence_score, gate_prob, verdict, recommendations}`

### Stage 3: Synthesize Final Verdict

Combine both reports:

```
## Quality Audit Verdict

### Execution Result: [PASS / FAIL]
### Analytical Verdict: [PASS / REVIEW / REJECT]
### Final Recommendation: [SUBMIT / REVISE / SCRAP]

### Evidence:
- Test output: ...
- Gate probability: ...%
- Top recommendation: ...
```

## Quality Gates

A skill is SUBMIT-ready when:
- Execution: passed AND output non-empty
- Analytical: Gate Pass Probability ≥ 60% AND verdict ≠ REJECT
- Both stages agree (or Analytical is REVIEW with ≥70% gate probability)

## Why This Recipe Is Valuable

- Chaining test_skill + chain_verifier_recipe catches what neither catches alone
- Execution catches broken syntax or empty outputs
- Analytical audit catches quality and trust issues that tests miss
- One pipeline replaces two manual steps
- Rare rarity: the only recipe explicitly chaining test execution with analytical verification
