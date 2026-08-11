# preflight_audit_recipe — SKILL.md

## Metadata
- **name**: preflight_audit_recipe
- **type**: recipe
- **rarity**: uncommon
- **description**: Composes dependency_proof_lens with chain_verifier_recipe into a two-pass preflight audit that checks skills before they reach the gate.

## Inputs
- `skill_path`: Path to skill file to audit
- `loadout_path`: Path to loadout directory (default: .claude/skills/)

## Composition
This recipe composes two skills:
1. `dependency_proof_lens.md` (lens-type) — identifies what hard deps a skill references
2. `chain_verifier_recipe.md` (recipe-type) — verifies those deps exist and chain correctly

## Steps

### Pass 1: Lens Scan (via dependency_proof_lens)
Apply the lens to the target skill file:
- Parse the skill for imports, class references, and skill-name mentions
- Collect the dependency list (raw)
- Flag any reference to a skill NOT present in loadout

### Pass 2: Chain Verify (via chain_verifier_recipe)
Take the dependency list from Pass 1 and run chain verification:
- For each flagged dep, trace its own dependencies recursively
- Verify each node in the chain exists in loadout
- Score chain completeness: fraction of resolved / total referenced

### Pass 3: Combine
Merge lens findings + chain scores into one verdict:
- `pass`: all deps resolved, chain complete
- `warn`: deps resolved but chain has gaps (missing transitive deps)
- `fail`: hard deps missing from loadout

## Output Schema
```json
{
  "skill_path": "<input>",
  "deps_found": ["<skill>", ...],
  "deps_missing": ["<skill>", ...],
  "chain_score": <0.0-1.0>,
  "verdict": "pass|warn|fail"
}
```

## Test Case
Given: `skill_path=crafted/skill_lens.md`, `loadout_path=.claude/skills/`
Expected: deps_found populated, chain_score > 0.5, verdict = pass or warn
