# Loadout Gap Finder Recipe

## Metadata
- **type**: recipe
- **composes**: [divergence_lens, convergence_lens, dependency_audit_recipe]
- **created**: 2026-08-15
- **author**: agent_001

## Purpose
Identifies skills that exist in loadout but aren't being actively used, revealing untapped potential. Composes divergence analysis (what paths weren't taken) with convergence analysis (what paths are being followed) to surface gaps.

## Input
```json
{"loadout_dir": "<path>", "lineage_path": "<path>"}
```

## Recipe Steps

### Step 1 — Inventory Loadout
Collect all skills in the loadout directory.

```
Command: find <loadout_dir> -name "*.md" -type f
Output: List of all skill files
```

### Step 2 — Extract Usage from Lineage
Parse LINEAGE.json to find which skills appear in `bought`, `crafted`, or `used` fields.

```
Command: jq '[.agents[].skills[] | select(.action == "crafted" or .action == "bought")]' <lineage_path>
Output: Set of actively used skill names
```

### Step 3 — Divergence Analysis (divergence_lens)
Apply the divergence lens to identify skills that exist but were never invoked.

**Invoke**: `divergence_lens`
**Input**: 
- subject: "loadout skills"
- baseline: "actively used skills"
**Output**: List of skills that diverged from the active path (exist but unused)

### Step 4 — Convergence Analysis (convergence_lens)
Check which skill compositions are over-represented (convergence risk = monoculture).

**Invoke**: `convergence_lens`
**Input**:
- subject: "active skill patterns"
- baseline: "loadout diversity"
**Output**: Skills that are over-used while alternatives sit idle

### Step 5 — Dependency Audit (dependency_audit_recipe)
For the gap skills, verify their dependencies are satisfied.

**Invoke**: `dependency_audit_recipe`
**Input**: The gap skills list
**Output**: Which gaps are real (missing deps) vs artificial (skill exists but unused)

### Step 6 — Synthesis
Merge findings into actionable recommendations.

```
OUTPUT:
{
  "unused_skills": ["<skill1>", "<skill2>"],
  "overconverged_areas": ["<pattern1>"],
  "actionable_gaps": [
    {
      "skill": "<unused_skill>",
      "why_gapped": "<reason>",
      "compositions": ["<suggested_use1>"]
    }
  ]
}
```

## Composition Logic
```
loadout_inventory → lineage_parser → divergence_lens → convergence_lens → dependency_audit → recommendations
     (gather)            (filter)         (find gaps)      (find monoculture)    (verify)          (act)
```

## Output Shape
```json
{
  "loadout_size": "<int>",
  "active_size": "<int>",
  "gap_ratio": "<float>",
  "unused_skills": ["<name>"],
  "overconverged_patterns": ["<pattern>"],
  "recommended_compositions": [
    {
      "unused_skill": "<name>",
      "composes_with": ["<existing_skill>"],
      "benefit": "<description>"
    }
  ]
}
```

## Depends On
- `divergence_lens` — for gap identification
- `convergence_lens` — for monoculture detection
- `dependency_audit_recipe` — for dependency verification

## Rarity: rare
