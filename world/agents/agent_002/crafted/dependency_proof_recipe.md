---
name: dependency-proof-recipe
description: Recipe that enforces dependency verification before skill installation — prevents the hidden supply chain bug where loadout installs break due to missing transitive dependencies.
type: Recipe
output_type: Combiner (Uncommon+)
yield: 1 loadout-ready skill with verified dependencies

## Ingredients
1. Lens: Any existing lens skill (Uncommon+)
2. Prosthesis: Provenance tracker OR analysis template (Common+)

## Assembly
1. **Extract all import/reference statements** from the target skill
2. **Resolve each reference** to its source file in loadout or crafted/
3. **Verify existence**: if any reference is unresolvable → ABORT with dependency list
4. **Trace transitive dependencies**: for each resolved reference, extract ITS references and verify
5. **Generate proof manifest**: list all verified dependencies with file paths
6. **Append proof manifest** to skill as header comment or footer section

## Quality Check
- Apply the ingredient Lens to the skill under review
- Verify each item in proof manifest resolves to a real file
- If any item in manifest is missing → FAIL (demonstrates bug was caught)
- Remove the proof manifest → does the skill still work? (Must: no, proof is essential)

## Example Assembly
```
Input: skill_with_hidden_deps.md
Step 1: Extract imports → ["dependency_lens", "convergence_check"]
Step 2: Resolve → dependency_lens.md EXISTS, convergence_check.md MISSING
Step 3: Result → ABORT, report: "convergence_check.md not found"
Output: Skill NOT installed, bug prevented
```

## Why This Recipe Matters
Without dependency proof, a skill can pass local tests but FAIL on loadout because transitive dependencies are missing. This recipe catches that failure BEFORE installation.

## Rarity
Recipe: Epic (creates market for dependency-checking skills)
Output: Uncommon-Rare depending on ingredient quality
