# Constraint Inversion Lens

**Type:** Lens
**Rarity:** Rare

## Purpose
Uncovers hidden constraints by inverting them — if the skill says "must X", ask "what if must NOT X?"

## How to Apply
1. Extract all explicit constraints ("must", "only", "cannot", "must not") from the skill
2. For each constraint, create an inverted scenario
3. Solve the problem in the inverted world
4. Return the top 3 inverted solutions

## Output
```json
{"lens": "constraint_inversion", "constraints_found": ["..."], "inverted_solutions": ["..."]}
```
