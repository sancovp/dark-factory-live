---
name: dependency_audit_recipe
description: Recipe that audits a skill for missing dependencies before loadout installation. Parses skill for imports/references, checks loadout, reports gaps.
type: recipe
version: 1.0.2
---

# Dependency Audit Recipe

**Type:** Recipe
**Purpose:** Verify a skill's dependencies exist in loadout BEFORE installation
**Addresses:** `dependency_proof_before_loadout` standing rule vulnerability

## Composition

This recipe composes:
1. **Skill parser** — extracts import/reference statements from skill markdown
2. **Loadout lister** — enumerates installed skills in loadout/
3. **Gap reporter** — formats missing dependencies as structured issues

## Input

```yaml
target_skill_path: "crafted/some_skill.md"
loadout_dir: "loadout/"
```

## Process

```python
import re
import os
from pathlib import Path

def dependency_audit_recipe(target_skill_path: str, loadout_dir: str = "loadout/") -> dict:
    """
    Audit a skill for missing dependencies.
    
    Returns:
        {
            "skill_path": str,
            "dependencies_found": [str, ...],
            "dependencies_satisfied": [str, ...],
            "gaps": [{"dep": str, "reason": str}, ...],
            "verdict": "INSTALLABLE" | "HAS_GAPS" | "UNVERIFIABLE"
        }
    """
    
    # STEP 1: Parse skill for dependencies
    deps = extract_dependencies(target_skill_path)
    
    # STEP 2: Enumerate loadout
    loadout_skills = list_loadout(loadout_dir)
    
    # STEP 3: Check each dependency
    gaps = []
    satisfied = []
    
    for dep in deps:
        if dep in loadout_skills:
            satisfied.append(dep)
        else:
            gaps.append({
                "dep": dep,
                "reason": f"'{dep}' not found in {loadout_dir}"
            })
    
    # STEP 4: Determine verdict
    if not deps:
        verdict = "UNVERIFIABLE"  # No deps detected - may be self-contained
    elif not gaps:
        verdict = "INSTALLABLE"
    else:
        verdict = "HAS_GAPS"
    
    return {
        "skill_path": target_skill_path,
        "dependencies_found": deps,
        "dependencies_satisfied": satisfied,
        "gaps": gaps,
        "verdict": verdict
    }


def extract_dependencies(skill_path: str) -> list:
    """
    Parse skill markdown for dependency references.
    
    Detects:
    - `requires: [skill1, skill2]` frontmatter (list items between --- markers)
    - `import <skill>` or `imports: <skill>` statements
    - `use <skill>` references  
    - skill path references like `skills/<name>/`
    """
    deps = []
    
    with open(skill_path) as f:
        content = f.read()
    
    # Frontmatter dependencies (YAML list items, exclude --- markers)
    fm_section = re.search(r'^---\s*\n(.*?)(?:^---)', content, re.MULTILINE | re.DOTALL)
    if fm_section:
        items = re.findall(r'^\s*-\s*(.+)', fm_section.group(1), re.MULTILINE)
        deps.extend([i.strip() for i in items if i.strip() != '---'])
    
    # Import/imports statements (flexible pattern)
    import_stmts = re.findall(r'(?:imports?:?)\s+([\w_-]+)', content, re.IGNORECASE)
    deps.extend(import_stmts)
    
    # Use statements
    use_stmts = re.findall(r'use\s+([\w_-]+)', content, re.IGNORECASE)
    deps.extend(use_stmts)
    
    # Skill path references
    skill_refs = re.findall(r'skills/([\w_-]+)/', content)
    deps.extend(skill_refs)
    
    # Remove duplicates and invalid entries
    return list(set(d for d in deps if d and d != '---' and not d.startswith('#')))


def list_loadout(loadout_dir: str) -> list:
    """
    Enumerate all skills in loadout directory.
    Returns list of skill names (without .md extension).
    """
    loadout = Path(loadout_dir)
    if not loadout.exists():
        return []
    
    skills = []
    for md_file in loadout.rglob("*.md"):
        skills.append(md_file.stem)  # filename without extension
    
    return skills


## Output Format

```yaml
verdict: HAS_GAPS
skill_path: crafted/chain_verifier_recipe.md
dependencies_found:
  - divergence_lens
  - convergence_lens
  - chain_verifier
dependencies_satisfied:
  - chain_verifier
gaps:
  - dep: divergence_lens
    reason: "'divergence_lens' not found in loadout/"
  - dep: convergence_lens
    reason: "'convergence_lens' not found in loadout/"
```

## Usage

```python
# Before installing any skill to loadout/
result = dependency_audit_recipe("crafted/my_new_skill.md")

if result["verdict"] == "INSTALLABLE":
    print("✓ All dependencies satisfied")
elif result["verdict"] == "HAS_GAPS":
    print(f"✗ Missing {len(result['gaps'])} dependencies:")
    for gap in result["gaps"]:
        print(f"  - {gap['dep']}: {gap['reason']}")
else:
    print("? No dependencies detected - verify manually")
```

## Gate Integration

Per `dependency_proof_before_loadout` rule:
> A skill that imports or references other components requires proof those dependencies exist in loadout BEFORE installation.

This recipe enforces that proof. Run BEFORE any `cp crafted/*.md loadout/` operation.

## Example Audit

```bash
# Audit a skill before buying/installing
python3 -c "
from dependency_audit_recipe import dependency_audit_recipe
import json

# Simulated check
result = dependency_audit_recipe('crafted/my_skill.md')
print(json.dumps(result, indent=2))
"
```

## Limitations

1. Only detects explicitly named dependencies
2. Does not verify DEPTH of dependency chains (A→B→C)
3. Does not check version compatibility
4. Loadout must exist at loadout_dir path

## Chaining

For depth-aware dependency chains, compose with `chain_verifier_recipe`.
