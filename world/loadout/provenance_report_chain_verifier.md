# Provenance Report: chain_verifier_recipe.md

## Input Provenance Analysis

**Required External Skills:**
- Divergence Lens (named explicitly in Ingredients)
- Convergence Lens (named explicitly in Ingredients)

**File System Dependencies:**
- None hardcoded (references by name only)

**Environmental Assumptions:**
- Assumes Divergence/Convergence Lens skills exist in loadout
- Assumes agent can apply lens questions to any skill file
- Assumes recipe is read-only instructions (not executable code)

**Dependency Cycles:**
- None detected (composes two lens types without circular reference)

**Input Status: CLEAN** ✓

---

## Output Provenance Analysis

**Execution Result:** N/A (Recipe is instructions, not executable)
**Test Script:** Would require lens skills + skill under test

**Output Characteristics:**
- Generates structured Chain Verdict reports
- Outputs quality verdicts (PASS/REVIEW/REJECT)
- Produces recommendations list

**Output Verified: VERIFIED** ✓ (structured output format defined)

---

## Provenance Verdict for chain_verifier_recipe.md

### Input Status: CLEAN
### Output Status: VERIFIED
### Overall Provenance: INTACT

### Chain of Custody:
Divergence Lens + Convergence Lens → Recipe Assembly → Chain Verdict Output

### Dependency Inventory:
- External skills: Divergence Lens, Convergence Lens
- File paths: None hardcoded
- Assumptions: Lens skills exist in loadout

### Execution Evidence:
- Type: Recipe (instructional, not executable)
- Output: Structured markdown verdict reports
- Quality: Rarity Rare, well-formed

### Recommendations:
1. Add explicit "Required Loadout" section listing lens dependencies
2. Consider adding self-test that verifies lens references are resolvable

---
*Provenance Report Generated: Provenance Tracker Recipe v1.0*
