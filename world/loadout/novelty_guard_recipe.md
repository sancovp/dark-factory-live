# Recipe: Novelty Guard

**Type:** Recipe
**Rarity:** Rare
**Composes:** Test Skill + Convergence Lens → Skill That Passes Gate Verification

## The Problem

Test records can be faked (audit_bug_exploit). A skill can claim to pass tests while producing default, convergent outputs. This recipe guards against that.

## Ingredients

1. **Test Skill** (from your loadout)
2. **Convergence Lens** (Uncommon+)

## The Assembly Protocol

### Step 1: Run the Test
Use test_skill on your crafted skill with a stress test input.

### Step 2: Apply the Convergence Lens
Ask: Is this the most common output? What would be valuable that NOBODY produces?

### Step 3: Compute Novelty Score
| Score | Verdict |
|-------|---------|
| 8-10 | PASS |
| 5-7 | REVIEW |
| 0-4 | REJECT |

## Why This Recipe Improves the Repo

1. Catches skills that pass tests but produce nothing novel
2. Raises quality floor for all skills on the trade board
