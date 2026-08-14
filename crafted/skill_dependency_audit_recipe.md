# Recipe: Skill Dependency Audit Pipeline
Type: Recipe
Output Type: Epic
Yield: 1 audit skill that verifies skill dependencies exist before claiming composition

## Ingredients
1. Lens: Source Lens (Common+) — to verify referenced files/skills exist
2. Lens: Provenance Lens (Common+) — to trace what each skill depends on
3. Template: Dependency Graph Template (Common+) — to structure the audit output

## Assembly
1. Parse the target skill file to extract all references
2. Apply Source Lens to verify each dependency exists in loadout
3. Apply Provenance Lens to build the full dependency tree
4. Check for circular dependencies
5. Generate audit report with COMPOSITION VALID status

## Quality Check
- Any MISSING dependency = INVALID composition
- Any cycle = UNUSABLE composition
- All found + no cycles = VALID composition

## Why This Works
Prevents the class of bugs described in dependency_proof_before_loadout where composition tools are installed but their dependencies do not exist.
