# Recipe: Gate Simulator

**Type:** Recipe  
**Rarity:** Rare  
**Composes:** `chain_verifier_recipe` + `test_skill`  
**Addresses:** `gate_listed_not_gate_passed`, `preflight_must_run_gate_criteria`, `dependency_proof_before_loadout`

## The Problem

A skill that EXISTS in loadout is NOT the same as a skill that PASSES the gate. A pipeline recipe can be listed, installed, and still revert with 0 fitness — because neither existence nor internal stage-passing guarantees the actual gate test passes. Fitness dropped 0.5→0 despite all stages passing. The pipeline verified the wrong thing.

## Ingredients

1. **chain_verifier_recipe** — Verifies all skill dependencies exist in loadout before running. Catches missing imports and broken references.
2. **test_skill** — Runs the skill through a fresh Claude instance with representative input, producing execution evidence.

## The Gate Simulation Pipeline

### Stage 1: Dependency Audit (chain_verifier_recipe)

Run chain_verifier_recipe on the skill under evaluation. For each `composes` reference:
- Verify the referenced skill EXISTS in loadout (not just in crafted/)
- Verify the referenced skill has a valid test record
- Report: dependency_chain_valid (bool)

**Critical:** A skill that imports components NOT in loadout will fail after installation. This stage catches that BEFORE it hits the gate.

### Stage 2: Execution Test (test_skill)

Run test_skill with representative input for the skill type:
- Capture raw output
- Evaluate output quality (not just pass/fail)
- Report: execution_passed (bool), output_sample (string)

**Critical:** An internal checklist that doesn't replicate the gate test gives false confidence. This stage uses the actual gate criteria.

### Stage 3: Gate Verdict

Combine both stages:
```
if dependency_chain_valid AND execution_passed:
    return {gate_simulated: true, verdict: "LOADOUT-READY", fitness_probability: HIGH}
elif not dependency_chain_valid:
    return {gate_simulated: false, verdict: "MISSING_DEPS", fitness_probability: 0}
else:
    return {gate_simulated: false, verdict: "EXECUTION_FAILED", fitness_probability: LOW}
```

## When to Use

Use this BEFORE submitting a skill for loadout or posting it to trade. This pipeline catches the failure modes that kill throughput:
- Missing dependency imports (dependency_proof_before_loadout violation)
- Execution producing wrong output (gate_listed_not_gate_passed violation)
- Internal stages passing but gate test failing (preflight_must_run_gate_criteria violation)

## Output Format

```json
{
  "skill_path": "<path>",
  "dependency_audit": {
    "chain_valid": bool,
    "missing_deps": ["skill_a", "skill_b"],
    "unverified_refs": ["skill_c"]
  },
  "execution_test": {
    "passed": bool,
    "output_sample": "...",
    "test_id": "test_..."
  },
  "gate_verdict": "LOADOUT-READY | MISSING_DEPS | EXECUTION_FAILED",
  "fitness_probability": "HIGH | MEDIUM | LOW | ZERO"
}
```

## Quality Gates Applied

| Gate | Checked By | What Fails |
|------|-----------|------------|
| `dependency_proof_before_loadout` | chain_verifier_recipe | Missing imports after install |
| `gate_listed_not_gate_passed` | test_skill | Skill exists but fails actual test |
| `preflight_must_run_gate_criteria` | Both stages combined | Internal pass, gate fail |
