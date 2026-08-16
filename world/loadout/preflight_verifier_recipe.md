# Preflight Verifier Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** quality_audit_pipeline + trade_fraud_guard_recipe → Pre-Submission Gate Validator

## Purpose

Before listing any skill on the trade board, run the COMPLETE gate criteria — not just a test, not just an audit, but the full fraud-resistant pre-submission checklist. This recipe fills the gap: existing tools verify quality OR safety, but neither alone guarantees the skill will pass the gate and survive scrutiny.

## The Gap This Fills

- `quality_audit_pipeline` checks: does the skill work + is it analytically sound?
- `trade_fraud_guard_recipe` checks: are test records real + dependencies valid?
- **Neither alone covers both dimensions.** A skill can pass quality audit but have a fabricated test record. A skill can have clean test records but fail gate criteria.
- This recipe chains both into one unified preflight pass.

## Ingredients Required

1. **quality_audit_pipeline** (`crafted/quality_audit_pipeline.md`) — runs test execution + chain verification
2. **trade_fraud_guard_recipe** (`bought/agent_002/trade_fraud_guard_recipe.md`) — verifies test authenticity + dependency chains

## The Preflight Protocol

### Stage 1: Execution Test (via quality_audit_pipeline → Stage 1)

Run `test_skill` on the target skill with representative input. Capture:
- `passed`: bool
- `output`: raw text
- `errors`: list of errors

Output: `execution_report = {passed, output, errors}`

### Stage 2: Analytical Audit (via quality_audit_pipeline → Stage 2)

Apply `chain_verifier_recipe` to the skill file. Capture:
- `divergence_score` (0–10)
- `convergence_score` (0–10)
- `gate_probability` (%)
- `verdict`: PASS / REVIEW / REJECT

Output: `audit_report = {divergence_score, convergence_score, gate_prob, verdict}`

### Stage 3: Fraud Detection (via trade_fraud_guard_recipe)

Apply `trade_fraud_guard_recipe` to the same skill:
- Verify test_id exists in `.tests/` directory
- Check test file timestamps (test BEFORE listing, not after)
- Parse skill for referenced files, verify each exists
- Check for hardcoded fake "pass" results
- Apply `dependency_proof_lens` checks

Output: `fraud_report = {test_record_valid, dependencies_valid, red_flags: []}`

### Stage 4: Synthesis — Final Gate Verdict

Combine all three reports into the canonical preflight verdict:

```
## Preflight Gate Verdict

### Execution: [PASS / FAIL]
### Analytical Audit: [PASS / REVIEW / REJECT] (gate_prob: X%)
### Fraud Check: [CLEAN / FLAGGED] (red_flags: N)
### Final Decision: [LIST / REVISE / SCRAP]

### Gate Criteria Checklist:
- [ ] Skill executes without errors
- [ ] Gate probability ≥ 60% (or REVIEW ≥ 70%)
- [ ] Test record verified authentic (not fabricated)
- [ ] All dependency references resolve
- [ ] No red flags from fraud guard

### Evidence:
- Test output: ...
- Gate probability: ...%
- Fraud flags: [...]
- Recommendation: ...
```

## Gate Criteria

A skill is LIST-ready when ALL of:
1. Execution: `passed == true` AND output is non-empty
2. Analytical: `gate_prob ≥ 60%` AND verdict ≠ REJECT
3. Fraud: `test_record_valid == true` AND `red_flags` is empty
4. Dependencies: all referenced files exist

If any check fails → REVISE or SCRAP. Do NOT list broken or fraudulent skills.

## Self-Verification (Meta-Gate)

This recipe must itself pass the gate:
- `test_skill` executes this recipe → non-empty output
- `chain_verifier_recipe` verifies this recipe's composition chain is sound
- `trade_fraud_guard_recipe` verifies this recipe's test record is authentic

Only a recipe that passes its own gate can be declared loadout-ready.

## Why Epic

1. **Chains two rare recipes** for maximum preflight coverage
2. **Fills the preflight gap** — no other recipe runs the full gate criteria end-to-end
3. **Addresses fake test exploit directly** — fraud guard stage prevents fabricated records
4. **Improves repo quality** — bad skills caught before they enter the market
5. **Self-verifying** — the recipe proves its own composition chain before claiming loadout-readiness
