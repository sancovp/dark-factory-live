# Dependency-Gate Validator Recipe

**Type:** Recipe
**Rarity:** Rare
**Composes:** dependency_lens + skill_type_gate_recipe → Loadout-Ready Skill Verifier

## Purpose

Before a skill is installed to loadout, it must pass TWO gates: (1) all declared dependencies exist in loadout, and (2) the skill's declared type matches its actual structure. This recipe combines dependency_lens (which finds what a skill claims to need) with skill_type_gate_recipe (which verifies type compliance) into a single pre-flight validator. A skill that passes both stages is safe to propose for loadout installation.

## Why This Composition Is Non-Obvious

Most agents verify EITHER type OR dependencies — not both. The standing rules establish that dependency gaps are loadout-breaking bugs AND that type fraud (declaring one type but producing another) is equally dangerous. Composing both lenses into a single pipeline catches the intersection: skills that are correctly typed but have missing dependencies, AND skills that declare dependencies but don't match their type.

## Ingredients Required

1. **dependency_lens** (`dependency_lens.md`) — Finds what a skill claims to depend on; reports missing loadout components
2. **skill_type_gate_recipe** (`skill_type_gate_recipe.md`) — Verifies a skill's declared type matches its actual structure; runs Meta-PE evaluation

## Pipeline Stages

### Stage 1: Dependency Audit (via dependency_lens)

Read `dependency_lens.md`. For the skill under evaluation:
1. Parse the skill file for import/reference statements (look for: `craft/`, `.md`, `skills/`, ingredient names)
2. Check each referenced component against the loadout directory
3. Run the lens process: `skill → dependency graph → loadout gap report`

Output: **Dependency Audit Report**
```json
{
  "skill_path": "<skill under evaluation>",
  "declared_deps": ["<component1>", "<component2>"],
  "loadout_deps_found": ["<component1>"],
  "missing_deps": ["<component2>"],
  "safe_for_loadout": false
}
```

**IF `safe_for_loadout == false`: STOP. Do not proceed to Stage 2.** File the missing dependency as a gap (per gap_filing_own_pr rule) before continuing.

### Stage 2: Type Compliance (via skill_type_gate_recipe)

Read `skill_type_gate_recipe.md` from the loadout. For the skill under evaluation:
1. Extract the declared type from the skill header (`**Type:**` field)
2. Run Stage 1 (Type Verification) of the gate recipe: verify the skill against its declared type's gate questions
3. Run Stage 2 (Fresh-Instance Test): get a test_id via `test_skill`
4. Run Stage 3 (Meta-PE Evaluation): provenance, failure modes, type check, novelty

Output: **Type Gate Report**
```json
{
  "skill_path": "<skill under evaluation>",
  "declared_type": "<Recipe/Lens/etc>",
  "type_compliance": "PASS/FAIL",
  "type_mismatches": [],
  "test_id": "<from Stage 2>",
  "meta_pe": {"provenance": "PASS", "failure_modes": [], "type_check": "PASS", "novelty": "score"},
  "verdict": "GATE_READY/NEEDS_REVISION/REJECT"
}
```

### Stage 3: Synthesis — Final Loadout Admission Verdict

Combine Stage 1 and Stage 2:

```json
{
  "skill_path": "<skill under evaluation>",
  "dependency_gate": {
    "safe_for_loadout": true,
    "missing_deps": [],
    "audit_passed": true
  },
  "type_gate": {
    "verdict": "GATE_READY",
    "test_id": "<id>"
  },
  "final_verdict": "LOADOUT_CANDIDATE / STOP_HERE",
  "blocking_issues": ["<if any>"],
  "recommendations": ["<2+ if STOP_HERE>"]
}
```

**LOADOUT_CANDIDATE**: Both dependency and type gates passed. Safe to propose for loadout installation.

**STOP_HERE**: One or both gates failed. Fix blocking issues before attempting loadout installation.

## Quality Gates

A skill is LOADOUT_CANDIDATE if and only if:
- [ ] Stage 1: `safe_for_loadout == true` (all declared deps exist in loadout)
- [ ] Stage 2: `type_compliance == PASS` (skill matches its declared type)
- [ ] Stage 2: `test_id` is a valid record from fresh-instance test
- [ ] Stage 2: Meta-PE `novelty > baseline` (skill is better than default)
- [ ] Stage 3: No blocking issues remain

## Why This Recipe Improves the Repo

Per the standing rules:
- `dependency_proof_before_loadout`: A skill that imports other components requires proof those dependencies exist in loadout BEFORE installation. This recipe provides that proof.
- `guard_must_pass_gate_to_be_loadout`: Any guard installed to catch dependency gaps must itself survive the gate test. This recipe documents the gate criteria for both dependency and type checking, making it self-verifying.
- `preflight_must_run_gate_criteria`: Preflight must exercise the actual gate test criteria. This recipe IS the preflight — it reproduces both the dependency audit and the type gate test criteria.

By running this pipeline before any skill is proposed for loadout installation:
1. Dependency gaps are caught before they cause gate reversions
2. Type fraud is caught before bad skills are shipped
3. The composition chain (dependency_lens → type_gate → verdict) is itself composition-proven

## Usage

```
1. Identify skill under evaluation: <path>
2. Read dependency_lens.md
3. Stage 1: Run dependency audit → if missing_deps: STOP, file gap issue
4. Read skill_type_gate_recipe.md from loadout
5. Stage 2: Verify type compliance + run test_skill + Meta-PE
6. Stage 3: Synthesize final verdict
7. If LOADOUT_CANDIDATE → safe to propose for loadout
8. If STOP_HERE → fix based on blocking_issues, return to Stage 1
```

## Rarity Justification

Rare because:
- Composes one crafted lens (dependency_lens) with one loadout recipe (skill_type_gate_recipe) — mixed provenance, non-trivial assembly
- Produces a qualitatively different output than either ingredient alone: dependency_lens alone misses type gaps; skill_type_gate_recipe alone misses dependency gaps
- Addresses a specific standing-rule gap: `dependency_proof_before_loadout` was established as a rule but no skill in loadout actually enforced it — this recipe does
- Self-verifying: the recipe describes the same gate criteria it must pass, creating alignment between the standard and the tool
