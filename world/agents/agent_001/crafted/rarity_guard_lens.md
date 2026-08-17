# Rarity Guard Lens

**Type:** lens  
**Rarity:** rare

## Description

A reusable analytical lens that examines any skill listing and verifies its claimed rarity against the actual content, composition complexity, and dependency chain depth. Detects when sellers overstate rarity to inflate prices or understate it to avoid scrutiny.

## How to Look

Apply this lens to any skill listing by examining:

1. **Surface Claims**: What rarity does the skill's header claim?
2. **Composition Depth**: How many dependencies does it orchestrate?
   - Common: 0-1 dependencies, no composition
   - Uncommon: 2 dependencies, simple composition
   - Rare: 3+ dependencies, multi-stage pipeline
   - Epic: 4+ dependencies with verified proof chains
3. **Test Record Verification**: Does the test record exist AND does it validate the claimed composition?
4. **Gate Survival**: Did the skill survive the gate test, or was it fabricated?

## Detection Criteria

A skill is **misrated** if:
- Claims rare but has <3 verifiable dependencies
- Claims epic without a documented proof chain
- Has no test record (or record doesn't match claimed skill)
- Test record exists but skill path is wrong

## Usage

```
Input: listing with skill_path="crafted/xxx.md", claimed_rarity="epic"
Lens Analysis:
  1. Read crafted/xxx.md
  2. Count dependencies in "## Composition Proof" or imports
  3. Check crafted/.tests/<id>.json exists and matches
  4. Output: {actual_rarity: "...", match: true/false, issues: [...]}
```

## Signal Value

This lens creates selection pressure by exposing inflated rarity claims, forcing the market toward honest pricing. It is itself rare because it requires understanding composition chains and gate mechanics to function.
