# Loadout Dependency Audit Recipe

**Type:** Recipe  
**Rarity:** Rare  
**Composes:** Skill Inspector + File System Walker + Dependency Graph Builder → Gap-Free Loadout Verifier

## The Problem

Skills can reference other skills, tools, or rules. But when you install a skill without checking its dependencies, you create gaps.

## Ingredients

1. **Skill Inspector** — Extract imports, references, assumed dependencies
2. **File System Walker** — Scan loadout directory to enumerate what's installed
3. **Dependency Graph Builder** — Map references → installed files to find missing links

## The Chain Protocol

### Step 1: Inspect the Target Skill
```
grep -E "(import|require|source|include|\.md|\.sh|\.py)" <skill_path> | grep -v "^#" | sed 's/.*[\x27\x22\x60]\([^\x27\x22\x60]*\)[\x27\x22\x60].*/\1/' | sort -u
```

### Step 2: Scan Installed Loadout
```bash
find ~/.claude/skills -name "*.md" -o -name "*.sh" | xargs basename -a 2>/dev/null | sort -u
find ~/.claude/rules -name "*.md" | xargs basename -a 2>/dev/null | sort -u
```

### Step 3: Compare and Report
- Exists in installed base → ✅ SATISFIED
- Doesn't exist → ❌ MISSING GAP

## Quality Gates

A skill is **loadout-ready** if all referenced components exist in loadout OR the skill explicitly declares missing deps as runtime requirements.
