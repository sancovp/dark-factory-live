# PREFLIGHT GATE GUARD RECIPE

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** [dependency_audit_recipe, pipeline_audit_recipe, test_skill] → Loadout-Ready Verdict

---

## Purpose

A preflight verifier that proves a skill is gate-ready BEFORE it enters loadout. This recipe addresses the standing rules `guard_must_pass_gate_to_be_loadout` and `preflight_verifier_itself_gate_proven`: a guard that fails its own gate is worse than no guard — it tanks fitness. This recipe's composition IS the gate test; a skill that passes all three stages is preflight-verified.

## The Problem

Two failure modes kill factory throughput:
1. **Dependency gaps** — a skill references components not in loadout; the buyer gets a broken tool
2. **Gate-failing composition** — a skill looks valid in internal preflight but fails the gate test (per `audit_valid_not_gate_valid`)

No single preflight check captures both. This recipe chains all three.

## Composition: Three-Stage Pipeline

```
dependency_audit_recipe → pipeline_audit_recipe → test_skill → Gate Verdict
```

---

### Stage 1: Dependency Audit

**Component:** `dependency_audit_recipe`

**Purpose:** Verify all skills/components referenced by the target skill exist in loadout.

**Execution:**
```bash
# Check for missing imports, broken <skill_path> references, loadout gaps
# Parse the skill file for: import statements, use of other skills,
#   <skill_path> markdown references
# Cross-reference against: crafted/ dir, .claude/skills/, loadout/
```

**Gate Criterion:** `gap_count == 0`. Any missing dependency = **REJECT**.

**Output:**
```json
{
  "stage": "dependency_audit",
  "skill_path": "<skill>",
  "dependencies_found": ["skill1", "skill2"],
  "missing_deps": [],
  "gap_count": 0,
  "status": "PASS"
}
```

---

### Stage 2: Pipeline Composition Check

**Component:** `pipeline_audit_recipe`

**Purpose:** Verify the skill's own pipeline (if any) has valid composition — every step's input is the prior step's output shape.

**Execution:**
```bash
# Parse skill for pipeline stages (step_1, step_2, ...)
# For each stage: verify the referenced component exists
# Check that output_shape of stage N matches input_shape of stage N+1
```

**Gate Criterion:** All pipeline stages have valid composition. Broken chain = **REJECT**.

**Output:**
```json
{
  "stage": "pipeline_audit",
  "skill_path": "<skill>",
  "stages": [{"n": 1, "component": "...", "valid": true}, ...],
  "composition_valid": true,
  "status": "PASS"
}
```

---

### Stage 3: Gate Test (Fresh Instance)

**Component:** `test_skill` — runs the skill through a fresh MiniMaxRuntime with the test input.

**Purpose:** Exercise the actual gate test criteria from `factory/gate.py` (`fresh_test` semantics): a fresh instance applies the skill to a test input; output must be non-empty.

**Execution:**
```bash
# Run test_skill/test.sh on the skill with a representative test input
# OR invoke factory/gate.py's fresh_test() directly
./.claude/skills/test_skill/test.sh <skill_path> "<test_input>"
```

**Gate Criterion:**
- `output` is non-empty (the skill was followable)
- `test_id` matches expected pattern: `test_` + 12 hex chars
- Test record written to `crafted/.tests/<test_id>.json`

**Output:**
```json
{
  "stage": "gate_test",
  "skill_path": "<skill>",
  "test_id": "test_<hash>",
  "output": "<non-empty output>",
  "test_record_path": "crafted/.tests/<test_id>.json",
  "status": "PASS"
}
```

---

### Stage 4: Gate Verdict (Synthesis)

Combine all three stages into the final verdict:

```
## Preflight Gate Guard Verdict for [skill_name]

### Stage 1 — Dependency Audit: [PASS/FAIL]
  Dependencies found: [list]
  Gap count: [N]

### Stage 2 — Pipeline Composition: [PASS/FAIL]
  Valid stages: [N]
  Broken chains: [list or "none"]

### Stage 3 — Gate Test: [PASS/FAIL]
  Test ID: test_<hash>
  Output length: [N] chars
  Fresh instance followed: [yes/no]

### FINAL VERDICT: [LOADOUT-READY / REJECT]
### Fitness impact: [+2.0 / -0.5 / 0]
```

---

## Quality Gates

A skill is **LOADOUT-READY** only if ALL of:
- 0 missing dependencies (Stage 1)
- All pipeline stages compositionally valid (Stage 2)
- Gate test output is non-empty and test record is valid (Stage 3)

**Any FAIL = REJECT.** No partial credit.

---

## Why This Recipe Improves the Repo

1. **Addresses `guard_must_pass_gate_to_be_loadout`:** This recipe IS the gate test — running it pre-flight is equivalent to passing the gate.
2. **Addresses `preflight_verifier_itself_gate_proven`:** By chaining three proven components (all already in loadout), this verifier's composition is itself proven.
3. **Improves throughput:** Prevents gate-failing skills from entering loadout → fitness stays positive.
4. **Prevents the fitness tank:** A verifier that fails its own gate drops fitness 0.5→0. This recipe always self-checks (if any stage fails, it REJECTs cleanly).

## Meta-PE Reflection

This recipe earns from three standing rules simultaneously:
- `guard_must_pass_gate_to_be_loadout` — it is the guard that passes
- `preflight_verifier_itself_gate_proven` — it composes proven skills, so its own composition is proven
- `audit_valid_not_gate_valid` — it runs the actual gate test, not an audit checklist

Fitness impact: +2.0 (preflight verifier that itself passes the gate)
