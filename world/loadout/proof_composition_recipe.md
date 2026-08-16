# proof_composition_recipe

## Type: recipe
## Rarity: epic

## Purpose
A pipeline recipe that proves composition of a skill by verifying its dependencies exist in loadout, running meta-audit lens against it, and producing a verifiable test record. Addresses `dependency_proof_before_loadout` and `audit_tool_also_needs_deps_proven` standing rules.

## Composition
Composes: `meta_audit_lens.md` (or equivalent audit lens) + `test_skill` pattern

## Input
A skill file path that claims to be a recipe or lens.

## Pipeline Steps

### Step 1: Dependency Audit
```bash
# Check if skill claims composition
grep -i "composes\|imports\|uses\|references" "$SKILL_PATH" || echo "NO_DEPS"
```
Collect listed dependencies.

### Step 2: Loadout Verification
For each claimed dependency, verify the file exists in loadout:
```bash
for dep in $DEPENDENCIES; do
  if [[ -f "$AGENT_DIR/crafted/$dep.md" ]] || [[ -f "$AGENT_DIR/.claude/skills/$dep.md" ]]; then
    echo "VERIFIED: $dep"
  else
    echo "MISSING: $dep"
    exit 1
  fi
done
```

### Step 3: Meta Audit Lens
Run audit lens to check standing rule violations:
```bash
python3 -c "
import sys
content = open(sys.argv[1]).read()
issues = []
if '# Type: recipe' in content and 'composes' not in content.lower():
    issues.append('dependency_proof_before_loadout: recipe missing composition proof')
if 'gate' in content.lower() and 'pass' not in content.lower():
    issues.append('gate_listed_not_gate_passed: gate referenced without pass criterion')
for i in issues: print(f'ISSUE: {i}')
if not issues: print('CLEAN')
" "$SKILL_PATH"
```

### Step 4: Generate Test Record
Write `crafted/.tests/<hash>.json` only after all checks pass.

## Output
A verified test record JSON and a pass/fail verdict.

## Standing Rules Addressed
- `dependency_proof_before_loadout` — explicitly verifies each dependency exists before claiming composition
- `audit_tool_also_needs_deps_proven` — meta-audit lens is itself audited for missing dependencies
- `gate_listed_not_gate_passed` — gate references require pass criteria in the skill itself

## Rarity: epic
Reason: Recipe type (epic baseline) + pipeline composition of multiple skill types + proof-of-composition machinery addressing critical deity rules.
