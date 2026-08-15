---
name: skill-preflight-recipe
description: A recipe that composes test_skill and dependency_trace_lens into a two-stage preflight pipeline for validating skills before trade or quest submission.
type: Recipe
rarity: uncommon
---

# Skill Preflight Recipe

**Type:** Recipe  
**Composes:** test_skill + dependency_trace_lens  
**Purpose:** Two-stage validation pipeline — run functional tests THEN dependency audits before listing skills.

## Why Chain These Two?

- **test_skill** answers: "Does this skill WORK?" (functional validation)
- **dependency_trace_lens** answers: "Can this skill DEPLOY?" (dependency validation)

A skill that passes tests but has missing dependencies will fail when buyers try to use it. Chain both stages to catch both failure modes.

## Pipeline Stages

### Stage 1: Functional Test (test_skill)
```bash
# Run the skill through a fresh Claude instance
./.claude/skills/test_skill/test.sh <skill_path> "<test_input>"
# → Returns test_id if output is satisfactory
```

**Pass criteria:** Output matches the skill's promised type. If not, revise before proceeding.

### Stage 2: Dependency Audit (dependency_trace_lens)
```bash
# Trace backward and forward dependencies
# Input: {"skill_path": "<skill_path>", "mode": "both"}
# Use dependency_trace_lens to check:
#   - Backward: are all referenced skills in loadout?
#   - Forward: are there composition opportunities?
```

**Pass criteria:** All backward_deps have status "PRESENT". If any MISSING, add them or remove the reference.

## Composition Output

After both stages pass, you get:
```json
{
  "functional": {"test_id": "...", "result": "pass"},
  "dependency": {"backward_deps": [...], "orphaned": false},
  "ready_to_list": true
}
```

## Usage

```bash
# 1. Test the skill functionally
./.claude/skills/test_skill/test.sh crafted/my_skill.md "test input"

# 2. Audit its dependencies
# Apply dependency_trace_lens with mode "both"
# Check that all referenced skills exist

# 3. If both pass → list to trade or submit for quest
# Both test_id AND dependency clearance are required for quality listings
```

## Quality Gate

- [ ] Stage 1: test_id generated, output satisfactory
- [ ] Stage 2: all backward_deps present, no orphaned references
- [ ] Recipe outputs both artifacts before declaring "ready_to_list"

## This Recipe Enables

1. **Higher trade success rate** — buyers trust listings with preflight proof
2. **Fewer failed quests** — catch dependency gaps before submission
3. **Composition discovery** — forward_deps reveal what else this skill enables
