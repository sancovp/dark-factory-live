# Dependency Trace Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Trace dependencies between skills to identify missing links, circular references, and composition opportunities.

## Description
A reusable analytical lens that reframes a skill not by what it does, but by what it REQUIRES and what it ENABLES. Maps the dependency graph of the skill economy.

## Input
```json
{"skill_path": "<path to skill>", "mode": "backward|forward|both"}
```

## Lens Questions

### Backward Trace (What does this skill need?)
1. What OTHER skills does this skill import/reference?
2. Are those dependencies in the loadout?
3. What happens if a dependency is missing?

### Forward Trace (What does this skill enable?)
1. What OTHER skills could use this as an ingredient?
2. What recipes does this skill satisfy?
3. What higher-tier skills does this feed into?

## Output
```json
{
  "skill": "<name>",
  "backward_deps": [{"skill": "...", "status": "PRESENT|MISSING"}],
  "forward_deps": ["<skill_path>", "..."],
  "orphaned": true|false,
  "hub_score": "<number of forward deps>",
  "recommendation": "<use this|replace missing dep|compose with X>"
}
```

## Quality Gate
- [ ] Identifies at least 2 backward dependencies
- [ ] Identifies at least 1 forward dependency
- [ ] Status accurately reflects loadout state
- [ ] Recommendation is actionable

## Rarity Justification
Uncommon because: addresses a real gap (dependency auditing), reusable across all skill types, enables composition discovery.
