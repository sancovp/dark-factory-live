# skill — composition_proof_recipe

## type
recipe

## description
Proves two or more skills compose end-to-end before declaring the pipeline loadout-ready. Scans skill files, resolves import/dep references, validates each link in the chain. Returns pass/fail with missing-dep list and cycle detection.

## composition
1. **scan** — glob for all `*.md` skill files in the target loadout dir
2. **parse** — extract `## composition` or `## depends_on` sections from each skill
3. **resolve** — check every referenced skill exists in loadout
4. **topo** — build dependency graph, detect cycles
5. **report** — emit JSON: `{pass: bool, missing: [], cycles: []}`

## steps
```python
import os, json, glob, re
from pathlib import Path

def composition_proof_recipe(loadout_dir: str) -> dict:
    loadout = Path(loadout_dir)
    skill_files = glob.glob(str(loadout / "*.md"))

    deps = {}   # skill_name -> set of dep names
    for f in skill_files:
        content = open(f).read()
        skill_name = Path(f).stem
        # Extract deps from composition or depends_on section
        section = re.search(r'## (composition|depends_on)\n(.*?)(?=\n## |\Z)', content, re.DOTALL)
        deps[skill_name] = set(re.findall(r'\*\*(.+?)\*\*', section.group(2))) if section else set()

    missing = []
    for skill, deps_set in deps.items():
        for d in deps_set:
            if not any(d.lower() in Path(p).stem.lower() for p in skill_files):
                missing.append(f"{skill} needs {d}")

    # Cycle detection via DFS
    cycles = []
    visited, stack = {}, {}
    def dfs(node, path):
        if stack.get(node):
            cycles.append(path[path.index(node):])
            return
        if visited.get(node): return
        visited[node] = True
        stack[node] = True
        for dep in deps.get(node, []):
            dfs(dep, path + [node])
        stack[node] = False

    for skill in deps:
        dfs(skill, [])

    return {"pass": len(missing) == 0 and len(cycles) == 0,
            "missing": missing, "cycles": cycles}
```

## input_schema
```yaml
loadout_dir:
  type: string
  description: Path to the loadout directory to validate
  default: .claude/skills
```

## output_schema
```yaml
pass:
  type: boolean
missing:
  type: array of string
cycles:
  type: array of array of string
```

## tags
- composition
- preflight
- dependency
- gate
