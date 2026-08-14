# Recipe: Dependency Gate Recipe
Type: Recipe
A composition skill that verifies a skill's dependencies exist before installation.

## Composes
1. **File Reader** — reads skill content to extract dependencies
2. **Pattern Matcher** — identifies dependency references (ingredients, imports, composition)
3. **Existence Verifier** — checks if each dependency exists in loadout

## Pipeline Logic
```
input_skill_path
  → File Reader (extract raw content)
  → Pattern Matcher (parse: ingredients, imports, composition sections)
  → Existence Verifier (check each dep in loadout paths)
  → output: {passed: bool, missing: [], present: []}
```

## Assembly Steps
1. **Read the skill file** at input_skill_path
2. **Extract dependencies** from:
   - `## Ingredients` or `Ingredients:` section (recipe format)
   - `## Composition` or `Composition:` section (pipeline format)
   - Any line matching `depends on`, `uses`, `imports`, or `[dependency_name]`
3. **Normalize each dependency** to skill name format (lowercase, underscores)
4. **Check loadout** for each dependency:
   - Check `crafted/` directory
   - Check `skills/` directory
   - Check `.claude/skills/` directory
5. **Report results** with missing dependencies blocking gate

## Inputs
- `input_skill_path`: path to skill to gate (e.g., "crafted/chain_verifier_recipe.md")

## Output
```json
{
  "skill": "<skill_name>",
  "passed": true/false,
  "missing": ["dep1", "dep2"],
  "present": ["dep3"],
  "recommendation": "INSTALL" or "BLOCK: missing dependencies"
}
```

## Quality Gate
This recipe itself must pass its own gate:
- Run dependency_gate_recipe on itself
- All three component skills must be listed as present or the recipe blocks itself

## When to Use
- Before installing any skill to loadout
- During audit of existing skills
- When debugging composition failures

## Rarity
Rare — provides essential safety net for composition-heavy systems.

## Why This Recipe Works
Per dependency_proof_before_loadout: "A skill that imports or references other components requires proof those dependencies exist in loadout BEFORE installation." This recipe provides that proof automatically.
