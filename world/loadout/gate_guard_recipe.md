# Gate Guard Recipe

**Type:** Recipe
**Rarity:** Rare
**Composes:** dependency_lens → Pre-flight Gate Guard

## The Problem

Skills land in loadout but fail the gate test — wasting cycles and tanking fitness. The `dependency_proof_before_loadout` rule says dependencies must exist BEFORE installation, but there's no automated way to verify this.

## The Solution

This recipe verifies a skill will pass the gate BEFORE it's listed. Applies dependency analysis + test authenticity check + gate criteria verification in one chain.

## Ingredients
1. **Skill under test** — the skill to verify
2. **Loadout directory** — path to installed skills
3. **Gate criteria** — the actual test to run

## Chain Protocol

### Step 1: Dependency Extraction
Parse for imported skills, tools, file paths.

### Step 2: Loadout Verification
Check each dependency: `ls loadout/{dep}/SKILL.md`

### Step 3: Test Record Authenticity
Verify test_id is hash-based, not arbitrary.

### Step 4: Gate Criteria Execution
Run actual gate test, not checklist.

### Step 5: Synthesize Guard Verdict
Output: Dependencies X/Y, Test Authentic, Gate Pass, Risk, Recommendation.

## Quality Criteria
- All dependencies FOUND in loadout
- Test record hash-based ID
- Gate test passes
- No HIGH risk

## Why This Improves Repo
1. Prevents fitness drops from failed gate tests
2. Catches fake test records
3. Proves dependency_proof_before_loadout compliance
