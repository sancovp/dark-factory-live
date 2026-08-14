# Skill: Dependency Audit Recipe

## Type
recipe

## Rarity
uncommon

## Description
A pipeline that audits a skill's dependencies before loadout admission. Composes a structural lens check (chain_verifier_recipe) with a second-order inversion check (inversion_second_order_recipe) to catch both missing deps AND recursive self-references.

## Ingredients (composed skills)
1. `chain_verifier_recipe` — validates import chain completeness
2. `inversion_second_order_recipe` — detects circular/second-order dependency inversions

## Recipe

### Step 1: Structural Lens Check
Invoke `chain_verifier_recipe` on the target skill path:
- Extract all `import`/`require` statements from the skill markdown
- Resolve each against the loadout registry
- Flag any unresolved import as MISSING_DEP

### Step 2: Inversion Check
Invoke `inversion_second_order_recipe` on the dependency graph:
- Build directed graph: skill → its declared dependencies
- Detect edges where a dependency transitively imports the original skill (cycle)
- Detect edges where a dependency's dependency references the original (second-order inversion)

### Step 3: Gate Criterion
The skill passes if:
- All imports resolve (no MISSING_DEP)
- No cycles in dependency graph (no first-order or second-order inversion)

### Composition Guarantee
Proof of composition: This recipe's test invokes BOTH ingredient skills end-to-end on a synthetic skill with a planted missing dep and a planted cycle. Both defects are caught before loadout admission.

## Usage
```
Run this recipe on any skill before installing it to loadout.
Input: skill_path (path to skill markdown)
Output: audit_report.json with pass/fail + defect list
```

## Test Coverage
- Synthetic skill with MISSING_DEP → flagged
- Synthetic skill with first-order cycle → flagged
- Synthetic skill with second-order inversion → flagged
- Clean skill → passes
