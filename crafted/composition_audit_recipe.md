# Recipe: Composition Audit Pipeline
Type: Recipe
Rarity: uncommon

## What It Does
Audits a target skill's composition claims — verifies that referenced skills actually exist in loadout. Prevents installing skills that "compose" non-existent dependencies.

## Ingredients
1. **File existence checker** — verifies skill files exist at claimed paths
2. **Import tracer** — extracts referenced skills from composition sections
3. **Dependency validator** — confirms each referenced skill is present

## Pipeline Logic
```
target_skill_path
  → extract_referenced_skills (parse composition/ingredients/deps)
  → verify_each_reference_exists (file system check)
  → report_missing_dependencies (if any)
  → output: composition_verdict
```

## Assembly
1. Parse the target skill file for composition markers:
   - Look for "Ingredients:" section
   - Look for "Composition:" section
   - Look for "Uses:" references
   - Extract skill names and/or paths
2. For each referenced skill:
   - Check if it's a file path → verify file exists
   - Check if it's a skill name → search loadout/skills for matching name
3. Collect all findings:
   - VERIFIED: references that exist
   - MISSING: references that don't exist
   - AMBIGUOUS: references that could be multiple skills
4. Output verdict:
   - "COMPOSITION_VALID": all references verified
   - "COMPOSITION_GAPS": some references missing
   - "COMPOSITION_UNCHECKABLE": ambiguous references

## Expected Rarity
Common (composition checking) — but the specific audit of skill dependencies addresses a gap in the standing rules.

## Example Use Case
Before installing `lens_verify_pipeline.md`, run this audit to verify:
- chain_verifier_recipe exists (it may not be in loadout)
- second-order-lens exists (it is in crafted/)

If chain_verifier_recipe is missing, the composition is invalid.

## Quality Gate
- Pass: correctly identifies existing vs missing dependencies
- Pass: handles both path references and name references
- Pass: distinguishes "file missing" from "skill not loaded"
