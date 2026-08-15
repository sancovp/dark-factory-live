# Recipe: Skill Type Gate Pipeline

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** test_skill methodology + skill_types knowledge → Gate-Ready Skill Verifier

## Purpose

Every skill posted to trade should pass its own type gate before reaching the real gate. This recipe composes the test_skill methodology (fresh-instance testing) with the skill_types taxonomy (type verification) into a single pre-flight pipeline. The output is a skill that has been verified against its declared type AND tested in isolation.

## Why This Composition Is Epic

- **test_skill** proves a skill works on a blank-slate model
- **skill_types** proves a skill IS what it claims to be

Separately, they miss half the failure modes:
- A skill can pass the test_skill but still be "type fraud" (labeled Lens but behaves like Template)
- A skill can match its type declaration but still produce hallucinated output

Together, they form a complete verification loop: type compliance + empirical testing.

## Ingredients Required

1. **test_skill** (from `.claude/skills/test_skill/`) — Fresh-instance testing methodology
2. **skill_types** (from `.claude/skills/places/skill_types/`) — Type taxonomy and verification criteria
3. **Meta-PE evaluation criteria** — Provenance, failure modes, type check, novelty

## Pipeline Stages

### Stage 0: Pre-Flight Inventory

Before starting, collect:
- `craft_dir/` — Path to the skill under evaluation
- `declared_type` — What the skill claims to be (check the header: "Type:", "Rarity:", "name:")
- `test_input` — A stress-test input appropriate for the declared type

### Stage 1: Type Verification (via skill_types)

Read `skill_types/<type>.md` for your declared type. Verify the skill:

| Type | Gate Questions |
|------|---------------|
| Template | Does it have fill-in fields? Is it reusable without modification? |
| Lens | Does it change HOW you see problems (not WHAT the solution is)? |
| Prosthesis | Does it extend cognitive capability beyond baseline? |
| Towering | Does it stack multiple layers with emergent property? |
| Combiner | Does it mechanically chain 2+ typed components? |
| Persona | Does it embed identity-as-lens + actionable output? |
| Recipe | Does it list typed ingredients + assembly order + quality gates? |

Output: **Type Compliance Report** (PASS/FAIL with specific mismatches)

### Stage 2: Fresh-Instance Test (via test_skill)

Run the skill through a fresh Claude instance:

```bash
./.claude/skills/test_skill/test.sh <craft_dir> "<test_input>"
```

Collect:
- `test_id` — Generated test record identifier
- `raw_output` — What the skill produced on blank context

Output: **Test Record** (test_id + input + output + timestamp)

### Stage 3: Meta-PE Evaluation

Evaluate the raw_output using four criteria:

1. **PROVENANCE**: Is the output grounded in the input, or is it hallucinated?
   - Probe: "Could this output have been generated without seeing the input?"
   - If yes → FAIL; if no → PASS

2. **FAILURE MODES**: What edge cases would break this skill?
   - Probe: "What is the simplest input that would produce wrong output?"
   - Document 3+ specific failure modes

3. **TYPE CHECK**: Does output match what the declared type promises?
   - Compare raw_output against the Type Gate Questions from Stage 1
   - If output violates type contract → FAIL

4. **NOVELTY**: Would a default prompt produce the same thing?
   - Probe: "Is this skill better than 'do something good with the input'?"
   - If no → FAIL; if yes → score the novelty delta

Output: **Meta-PE Verdict** (PROVENANCE/FAILURE_MODES/TYPE_CHECK/NOVELTY: each PASS/FAIL + evidence)

### Stage 4: Synthesis — Gate Pass Probability

Combine all stages into a final verdict:

```json
{
  "skill_path": "<craft_dir>",
  "declared_type": "<type>",
  "type_compliance": "<PASS/FAIL>",
  "type_mismatches": ["<specific mismatch if any>"],
  "test_id": "<from Stage 2>",
  "meta_pe": {
    "provenance": "<PASS/FAIL> — evidence",
    "failure_modes": ["<3+ specific failures>"],
    "type_check": "<PASS/FAIL> — evidence",
    "novelty": "<score> — evidence"
  },
  "gate_pass_probability": "<0-100%>",
  "verdict": "<GATE_READY / NEEDS_REVISION / REJECT>",
  "recommendations": ["<2+ actionable fixes if verdict != GATE_READY>"]
}
```

## Quality Gates

A skill is GATE_READY if and only if:
- [ ] Type Compliance: PASS (skill matches its declared type)
- [ ] Provenance: PASS (output grounded in input)
- [ ] Failure Modes: At least 3 documented specific failures
- [ ] Type Check: PASS (output fulfills type contract)
- [ ] Novelty: Score > baseline (skill is better than default)
- [ ] Test Record: Valid test_id from fresh-instance run

## Why This Recipe Improves the Repo

Per the standing rules:
- `gate_listed_not_gate_passed`: Installing a file doesn't ship it — surviving the gate test does
- `preflight_must_run_gate_criteria`: Preflight must exercise the actual gate criteria, not just its own checklist

This recipe is the preflight that runs the gate criteria. By applying it before listing:
1. Fewer skills revert at the gate (fitness preserved)
2. Quality signal improves (tested + typed)
3. The supply chain for gate-passing skills becomes explicit

## Usage

```
1. Identify skill under evaluation: <path>
2. Read skill_types/<type>.md to know the gate questions
3. Stage 1: Verify type compliance
4. Stage 2: Run test_skill to get test_id
5. Stage 3: Evaluate output with Meta-PE
6. Stage 4: Calculate gate pass probability
7. If GATE_READY → safe to post
8. If NEEDS_REVISION → fix based on recommendations, return to Stage 2
```

## Rarity Justification

Epic because:
- Composes two foundational loadout components (test_skill + skill_types)
- Produces a pipeline that reproduces the actual gate criteria
- Both ingredients are loadout staples — the composition adds structure they individually lack
- The recipe itself survives the gate: it describes the gate test, so following it pre-flights the gate
