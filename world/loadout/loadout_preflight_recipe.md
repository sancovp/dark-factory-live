# Loadout Preflight Recipe

## Metadata
- **type**: recipe
- **rarity**: uncommon
- **composes**: chain_verifier_recipe + test_skill

## The Problem

The `dependency_proof_before_loadout` rule states: "A skill that imports or references other components requires proof those dependencies exist in loadout BEFORE installation."

Currently, audit tools catch failures AFTER install. This wastes cycles and causes reverts. This recipe runs the gate BEFORE declaring loadout-ready.

## Ingredients

1. **chain_verifier_recipe** — Verifies dependency chain completeness and quality scores
2. **test_skill** — Verifies the skill actually executes and produces output

## The Pipeline

### Stage 1: Dependency Verification (chain_verifier_recipe)

Invoke `chain_verifier_recipe` on the target skill:
- Extract all `import`/`require` statements from skill markdown
- Resolve each against loadout registry
- Check divergence/convergence scores
- Output: `{deps_ok: bool, missing_deps: [], scores: {...}}`

### Stage 2: Execution Verification (test_skill)

Invoke `test_skill` on the same skill:
- Run skill with sample input
- Verify non-empty output
- Output: `{exec_ok: bool, output: str, errors: []}`

### Stage 3: Preflight Verdict

Combine both results:

```
LOADOUT-READY if:
  - deps_ok == true (all dependencies exist)
  - exec_ok == true (skill produces output)
  - convergence_score >= 5 (minimum quality threshold)

BLOCKED if:
  - Any missing dependencies
  - Execution fails or produces empty output
  - Quality scores below threshold
```

## Why This Recipe Is Valuable

- Composes chain_verifier_recipe + test_skill for comprehensive pre-loadout check
- Catches dependency gaps BEFORE installation (saves cycle on revert)
- Verifies both structure (deps exist) AND behavior (skill runs)
- Satisfies `dependency_proof_before_loadout` rule with end-to-end proof
- Different from quality_audit_pipeline: focuses on dependency proof, not just quality

## Usage

```bash
# Run preflight check before installing to loadout
python loadout_preflight_recipe.py --skill-path crafted/my_skill.md
```

## Test Coverage

- Skill with all deps resolved → PASSES preflight
- Skill with missing deps → BLOCKED (dependency_proof_before_loadout)
- Skill with empty output → BLOCKED (execution fails)
- Skill below quality threshold → BLOCKED (convergence_score < 5)
