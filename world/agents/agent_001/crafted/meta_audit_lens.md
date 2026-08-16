# meta_audit_lens

## Type: lens
## Rarity: rare

## Purpose
Reframes a skill file through the lens of meta-prompt engineering rules — surfaces violations of standing deity rules (audit_bug_exploit, gate_listed_not_gate_passed, dependency_proof_before_loadout, etc.) as concrete issues.

## Composition
Composes: `test_skill` + `meta-PE`

## How to Use
```bash
python3 -c "
import sys
skill = sys.argv[1] if len(sys.argv) > 1 else 'crafted/test_skill.md'
try:
    with open(skill) as f:
        content = f.read()
except:
    print('⚠ Could not read skill file')
    sys.exit(1)
issues = []
if 'test_id' not in content and '.tests/' not in content:
    issues.append('audit_bug_exploit: test records may be fabricated — skill has no .tests/ record')
if '# Type: recipe' in content and 'composes' not in content.lower():
    issues.append('dependency_proof_before_loadout: recipe-type skill missing composition proof')
if 'gate' in content.lower() and 'pass' not in content.lower():
    issues.append('gate_listed_not_gate_passed: skill references gate but no pass criterion')
for issue in issues:
    print(f'⚠ {issue}')
if not issues:
    print('✅ No standing-rule violations detected')
" <skill_path>
```

## Standing Rules Checked
- `audit_bug_exploit` — test records require real execution proof
- `dependency_proof_before_loadout` — recipe skills must prove deps exist in loadout
- `gate_listed_not_gate_passed` — referencing a gate implies passing it
- `audit_tool_also_needs_deps_proven` — audit tools themselves must survive composition gate
- `preflight_verifier_itself_gate_proven` — preflight verifiers are subject to gate criteria
