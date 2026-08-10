# Gate Test Preflight Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** Test Skill + Loadout Dependency Verifier → Gate-Tested Skill

## The Problem

Skills fail the gate not because they're bad, but because the preflight didn't run the actual gate criteria. The preflight pipeline passes all stages but tests the wrong thing → fitness drops 0.5→0 despite "passing". The fix: preflight must run OR replicate the real gate test, not just its own checklist.

## The Rule This Recipe Enforces

> **preflight_must_run_gate_criteria**: A preflight pipeline that passes internal stages but doesn't exercise the actual gate test gives false confidence. Preflight must run or replicate the real gate test criteria, not just its own checklist.

## Ingredients

1. **Test Skill** (Common+) — Runs skill through fresh instance, captures output
2. **Loadout Dependency Verifier** (from dependency_proof_before_loadout) — Ensures deps exist

## Assembly Protocol

### Step 1: Run Test Skill

Execute the target skill through test_skill with gate-relevant input:

```bash
./.claude/skills/test_skill/test.sh <skill_path> "<gate_test_input>"
```

Capture: test_id, raw output, timestamp

### Step 2: Verify Loadout Dependencies

Run Loadout Dependency Verifier on the skill:

```bash
# Scan for skill references
grep -E "(skill|component|recipe|lens)" <skill_path> | grep -iE "(uses?|composes?)"

# Verify each exists in loadout
for dep in <references>; do
  find loadout/ -name "*${dep}*" -type f
done
```

### Step 3: Replicate Gate Criteria Check

Run the actual gate test (or closest proxy):

```bash
# If gate test exists:
<gate_test_command> <skill_path>

# If no gate test, run proxy:
# 1. Does skill produce output on blank input?
# 2. Does skill handle edge cases?
# 3. Does skill type match output format?
```

### Step 4: Generate Gate-Compliance Report

```markdown
## Gate Test Preflight Report for [skill_name]

### Test Skill Result: [PASS/FAIL]
### Dependency Verifier Result: [PASS/FAIL]
### Gate Criteria Check: [PASS/FAIL]

### Overall Gate Readiness: [READY/NOT READY]
### Blocking Issues: N
### Recommendations:
1. ...
```

## Quality Gates

A skill is GATE-READY only if:
- Test skill produces non-empty output
- All dependencies verified in loadout
- Gate criteria (or proxy) returns PASS
- ANY single FAIL = NOT READY until resolved

## Why This Recipe Improves the Repo

1. **Prevents fitness drops**: Real gate criteria run before listing
2. **Eliminates false confidence**: Pre-flight passes only if actual gate passes
3. **Saves throughput**: Bad skills caught before wasting gate cycles
4. **Enforces two rules**: preflight_must_run_gate_criteria + dependency_proof_before_loadout

## Composition Verification

This recipe COMPOSES two smaller skills:
1. `test_skill` — runs fresh-instance test
2. `loadout_dependency_verifier_recipe` — verifies dependencies

Both must exist before this recipe can be used.
