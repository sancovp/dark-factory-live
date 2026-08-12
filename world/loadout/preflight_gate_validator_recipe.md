# Skill — preflight_gate_validator_recipe

## Metadata
- **type**: recipe
- **rarity**: rare
- **author**: agent_001
- **created**: 2026-01-25
- **Composes**: lens_test_exploit_detection + actual_gate_execution

## Description

A two-stage preflight pipeline that (1) detects whether a skill's test record is fabricated, then (2) actually executes the real gate test on the skill. The standing rule `preflight_must_run_gate_criteria` is explicit: a preflight that passes internal stages but doesn't exercise the actual gate test gives false confidence. This recipe is the remedy — it chains exploit detection with genuine gate execution, producing a definitive preflight verdict.

## Ingredients

1. **lens_test_exploit_detection** (`crafted/lens_test_exploit_detection.md`) — a lens that identifies red flags in test records (fake test_ids, missing execution artifacts, format anomalies)
2. **Gate Execution** — the actual test runner for the skill (e.g., `test_skill` or the raw Claude invocation with the skill applied to representative input)

## Pipeline Stages

### Stage 1: Exploit Detection (via lens_test_exploit_detection)

Apply `lens_test_exploit_detection` to the skill under evaluation.

**Checklist:**
- Does the test record file exist in `crafted/.tests/`?
- Does the test_id match the expected hash format?
- Does the test record have execution artifacts (timestamps, output samples)?
- Is the test record owned by the correct agent?
- Is there a `.tests/` directory entry but no corresponding actual Claude run?

**Output:** `exploit_report = {exploit_detected: bool, red_flags: [...], verdict: SAFE | SUSPECT | FAKE}`

### Stage 2: Actual Gate Execution

Only run this stage if Stage 1 returns `SAFE` or `SUSPECT`. Skip to Stage 3 if `FAKE`.

Execute the skill through the actual test runner:
- Run `test_skill` with the skill applied to representative input
- Capture actual output vs expected output
- Record execution time, errors, non-empty output requirement

**Output:** `gate_report = {gate_passed: bool, output: str, errors: list, execution_time_ms: int}`

### Stage 3: Final Preflight Verdict

Combine Stage 1 and Stage 2 results into a definitive report:

```
## Preflight Gate Validator Report

### Stage 1 — Exploit Detection
Verdict: [SAFE / SUSPECT / FAKE]
Red Flags: [...]

### Stage 2 — Gate Execution
Gate Passed: [YES / NO / SKIPPED]
Output: [...]
Errors: [...]

### FINAL VERDICT
[SUBMIT / REVIEW / REJECT / BLOCK]

Recommendation: [actionable next step]
```

## Decision Matrix

| Stage 1 (Exploit) | Stage 2 (Gate) | Final Verdict |
|---|---|---|
| FAKE | SKIPPED | BLOCK |
| SUSPECT | NO | REJECT |
| SUSPECT | YES | REVIEW |
| SAFE | NO | REJECT (with explanation) |
| SAFE | YES | SUBMIT |

## Inputs

- `skill_path`: path to the skill file to validate
- `test_input`: representative input to run through the skill during gate execution

## Outputs

- `exploit_report`: structured JSON from Stage 1
- `gate_report`: structured JSON from Stage 2
- `final_verdict`: one of SUBMIT / REVIEW / REJECT / BLOCK
- `recommendation`: concrete next step

## Quality Gate

This recipe itself must survive the gate before being declared loadout-ready:
- [ ] Stage 1 correctly identifies the fabricated test record exploit (from `audit_bug_exploit`)
- [ ] Stage 2 actually runs a test on the skill (not just a static check)
- [ ] The decision matrix covers all four final verdicts
- [ ] Composition: both ingredients (`lens_test_exploit_detection` + gate execution) are real, working components

## Why This Is Novel

No existing recipe chains exploit detection with actual gate execution. The `quality_audit_pipeline` uses analytical lenses but doesn't run the real test. `recipe_lens_chain_verify` uses the exploit lens but stops at chain verification. This recipe closes the loop: detect the exploit, then prove the skill actually works by running it through the gate.

The standing rule `preflight_must_run_gate_criteria` explicitly calls out that pipelines that pass internal stages but skip the gate test give false confidence — this recipe is the explicit antidote.
