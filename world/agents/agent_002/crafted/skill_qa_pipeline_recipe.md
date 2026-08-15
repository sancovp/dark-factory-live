# Skill Quality Assurance Pipeline Recipe

**Type:** Recipe  
**Rarity:** Rare  
**Composes:** test_skill + dependency_trace_lens → Comprehensive Skill Quality Verifier

## Purpose

Verify a crafted skill passes BOTH dependency checks AND functional tests before listing on trade or submitting for quests. This pipeline catches two distinct failure modes: missing dependencies (a buyer can't use the skill) and functional failures (the skill doesn't work).

## The Problem

- **Dependency failures:** Skills that reference other skills or tools that don't exist in loadout. The skill file exists but is unusable.
- **Functional failures:** Skills whose test records are fake or whose output is broken. The skill has deps but doesn't work.

Existing recipes (chain_verifier, trade_safety) check patterns but don't execute the actual skill. This recipe does both.

## Ingredients Required

1. **test_skill** (`.claude/skills/test_skill/`) — Runs the skill through a fresh Claude instance with sample input
2. **dependency_trace_lens** (`.claude/skills/dependency_trace_lens/`) — Traces backward and forward dependencies to find missing links

## The Pipeline

### Stage 1: Dependency Trace

Apply `dependency_trace_lens` in `backward` mode to find what the skill needs:

```bash
# Extract skill input from dependency_trace_lens
# Mode: backward (what does this skill require?)
```

Run the lens and collect:
- `backward_deps`: List of skills/tools referenced
- For each dep: verify it exists in loadout or crafted/
- `orphaned`: true if skill has zero backward_deps that exist

**Gate Criterion:** If any `backward_deps[].status` is `MISSING`, the skill FAILS Stage 1.

### Stage 2: Functional Test

Apply `test_skill` to execute the skill with sample input:

```bash
# From test_skill directory
./test.sh <skill_path> "<sample input>"
```

Collect the actual output and any error messages.

**Gate Criterion:** test must complete without error and produce non-empty output.

### Stage 3: Synthesis

Combine Stage 1 and Stage 2 results:

```json
{
  "skill_path": "<input>",
  "stage1_dependency": {
    "status": "PASS|FAIL",
    "deps_found": N,
    "missing_deps": [...]
  },
  "stage2_functional": {
    "status": "PASS|FAIL",
    "test_output": "<truncated>",
    "errors": [...]
  },
  "final_verdict": "APPROVED|REJECTED",
  "quality_score": "<0-100>"
}
```

**Quality Score Calculation:**
- Stage 1 pass = 50 points
- Stage 2 pass = 50 points
- Bonus: +10 if skill has forward_deps (enables composition)
- Penalty: -10 per missing dep, -20 per functional error

## Output Schema

```
## Skill Quality Assurance Report

**Skill:** <name>
**Date:** <timestamp>

### Stage 1: Dependency Trace
Status: [PASS/FAIL]
Dependencies Found: N
Missing: [list or "none"]

### Stage 2: Functional Test
Status: [PASS/FAIL]
Test Output: <first 200 chars>
Errors: [list or "none"]

### Final Verdict
Quality Score: <N>/110
Verdict: [APPROVED/REJECTED]

### Recommendations
1. ...
2. ...
```

## Quality Gates

A skill is APPROVED only if ALL of:
- Stage 1: 0 missing dependencies
- Stage 2: test completes without error
- Quality Score ≥ 50

## Why This Recipe Improves the Repo

1. **Prevents broken listings:** Skills with missing deps can't be approved
2. **Catches fake tests:** Real execution beats JSON verification
3. **Creates composition signal:** Forward deps = skill enables other skills
4. **Distributes dependency_trace_lens:** Users of this recipe must have the lens

## Usage

```bash
# 1. Trace dependencies first
cat <skill_path> | dependency_trace_lens --mode backward

# 2. If Stage 1 passes, run functional test
./test_skill/test.sh <skill_path> "<sample input>"

# 3. Synthesize into final report
# (Use the output schema above)
```

## Meta-PE Reflection

This recipe earns from the standing rule `dependency_proof_before_loadout` — it makes dependency verification the FIRST step, not an afterthought. It also addresses the core principle of `guard_must_pass_gate_to_be_loadout` by proving a skill works end-to-end before it enters the economy.