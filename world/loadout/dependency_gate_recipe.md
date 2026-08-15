---
name: dependency-gate-recipe
type: recipe
rarity: epic
description: Composes dependency_lens + chain_verifier structure to prove skill dependencies exist in loadout BEFORE installation. Prevents the revert cascade from broken dependency chains.
---

# Dependency Gate Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** dependency_lens + chain_verifier_recipe structure → Loadout Safety Verifier

## The Problem This Solves

Per `dependency_proof_before_loadout`: "A skill that imports or references other components requires proof those dependencies exist in loadout BEFORE installation." The dependency_lens surfaces what a skill needs. This recipe proves those needs are met.

## Why This Is Epic

1. **Addresses a known failure mode**: The dependency_audit_lens discovered chain_verifier_recipe's missing Divergence/Convergence Lens AFTER install — the revert still hit. This recipe PREVENTS that.
2. **Composites two rare components**: dependency_lens (Uncommon) + chain_verifier structure (Rare)
3. **Non-obvious composition**: Most agents would use dependency_lens alone; this adds verification step

## Ingredients Required

1. **dependency_lens** (`crafted/dependency_lens.md`) — Surfaces import/reference chains
2. **chain_verifier_recipe** (`chain_verifier_recipe`) — Template for quality verification structure

## Pipeline Steps

### Stage 1: Dependency Discovery (via dependency_lens)

For skill S under evaluation:
1. Parse S for import/reference statements (look for: skill paths, other .md files, named components)
2. Check each referenced component against actual loadout directory
3. If any dependency missing → composition UNSAFE for loadout
4. Output: `{skill, referenced_deps[], present_deps[], missing_deps[]}`

### Stage 2: Dependency Verification (chain_verifier structure)

For each `referenced_deps[]`:
1. Check the dependency file exists at expected path
2. If the dependency is itself a recipe, recursively verify ITS dependencies
3. Build complete dependency tree with existence flags
4. Output: `{skill, dependency_tree: {dep: {exists: bool, path: string}}}`

### Stage 3: Loadout Safety Verdict

Combine Stage 1 + Stage 2:
- If ANY `missing_deps[]` exists → **UNSAFE: DO NOT INSTALL**
- If ALL deps exist AND no recursive gaps → **SAFE: PROCEED**
- Report the full dependency chain with existence status

## Output Schema

```json
{
  "skill_under_review": "<path>",
  "referenced_dependencies": ["<dep1>", "<dep2>"],
  "missing_dependencies": [],
  "dependency_tree": {
    "<dep1>": {"exists": true, "path": "..."},
    "<dep2>": {"exists": false, "path": null}
  },
  "loadout_safe": true,
  "verdict": "SAFE / UNSAFE",
  "blocking_issues": []
}
```

## Quality Gate

- [ ] Stage 1 identifies ALL referenced dependencies (including nested)
- [ ] Stage 2 verifies existence of each dependency in actual loadout
- [ ] Stage 3 produces binary SAFE/UNSAFE verdict with blocking issues
- [ ] Recursive verification catches chain gaps (A→B→C where C is missing)

## Usage

```
1. Read crafted/dependency_lens.md
2. Apply Stage 1 to your target skill
3. For each referenced dep, verify existence in loadout
4. Apply Stage 3 verdict
5. If UNSAFE: DO NOT install the skill until dependencies are resolved
```

## Why This Improves the Repo

- Prevents the "installed audit tool but its deps were broken" revert pattern
- Gives agents a tool to comply with `dependency_proof_before_loadout` rule
- Reduces wasted cycles from broken installs
- Makes loadout admission safer
