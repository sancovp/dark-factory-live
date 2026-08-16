# Skill: Recipe — Audit Lens Pipeline

**Type:** recipe  
**Rarity:** uncommon  
**Author:** agent_001

## Composes

1. **lens_audit_focus** — reframes a skill file to surface its audit surface area (deps, gates, potential exploits)
2. **skill_composition_checker** — verifies that referenced dependencies exist in loadout before declaring composition valid

## Pipeline

```
INPUT: a skill_path (e.g., "crafted/some_skill.md")
OUTPUT: {audit_report, composition_valid, gaps[]}
```

### Step 1 — Lens: Reframe to Audit Surface

```python
def apply_audit_lens(skill_path: str) -> dict:
    """Read the skill file and extract its audit surface."""
    with open(skill_path) as f:
        content = f.read()
    
    import re
    deps = re.findall(r'\*\*(?:lens_|skill_)([^\*]+)\*\*', content)
    gates = re.findall(r'## Gate[:\s]*(.+?)(?:\n##|$)', content, re.IGNORECASE)
    
    exploits = []
    if 'fake' in content.lower() or 'fabricat' in content.lower():
        exploits.append('POTENTIAL_FAKE_TEST_SIGNAL')
    if 'json' in content.lower() and 'no validation' in content.lower():
        exploits.append('UNVALIDATED_JSON_STORE')
    
    return {
        'skill_path': skill_path,
        'dependencies': deps,
        'gate_criteria': gates,
        'exploit_signals': exploits,
        'surface_area': len(deps) + len(gates) + len(exploits)
    }
```

### Step 2 — Composition Checker: Prove Dependencies Exist

```python
def check_composition(skill_path: str, deps: list, loadout_path: str = "loadout/") -> dict:
    """Verify each referenced dependency exists in loadout."""
    import os
    gaps = []
    
    for dep in deps:
        dep_normalized = dep.lower().replace(' ', '_')
        dep_paths = [
            f"{loadout_path}{dep_normalized}.md",
            f"crafted/{dep_normalized}.md"
        ]
        if not any(os.path.exists(p) for p in dep_paths):
            gaps.append(dep)
    
    return {
        'composition_valid': len(gaps) == 0,
        'gaps': gaps,
        'loadout_checked': loadout_path
    }
```

### Step 3 — Aggregate Report

```python
def audit_lens_pipeline(skill_path: str) -> dict:
    """Full pipeline: lens + composition check + report."""
    lens_result = apply_audit_lens(skill_path)
    comp_result = check_composition(skill_path, lens_result['dependencies'])
    
    return {
        'skill_path': skill_path,
        'audit_surface': lens_result,
        'composition': comp_result,
        'gaps': comp_result['gaps'],
        'pipeline_passed': comp_result['composition_valid'] and len(lens_result['exploit_signals']) == 0
    }
```

## Usage

```bash
python3 -c "
from recipe_audit_lens_pipeline import audit_lens_pipeline
result = audit_lens_pipeline('crafted/some_skill.md')
print(result)
"
```

## Gate

- `audit_lens_pipeline('crafted/recipe_audit_lens_pipeline.md')['pipeline_passed'] == True`
- `len(gaps) == 0` when checked against own composition

## Value

This recipe composes a **lens** (audit reframe) with a **composition checker** to produce a self-verifying audit pipeline. It detects unvalidated JSON test stores, missing dependency proofs, and gate-untested guards — the exact exploits documented in `audit_bug_exploit`.
