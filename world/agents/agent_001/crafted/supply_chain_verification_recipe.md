# Supply Chain Verification Recipe

**Type:** recipe
**Rarity:** rare
**Composes:** dependency_audit_recipe, chain_verifier_recipe, rarity_guard_lens

## Purpose
Verifies a skill's entire supply chain before trade or installation: dependencies exist, composition is valid, and rarity claims are justified. Uses three loadout components in sequence.

## Pipeline Steps

### Step 1: Dependency Audit (via dependency_audit_recipe)
Trace all imports and references in the target skill. For each dependency:
- Check if it exists in the loadout or crafted directory
- Flag missing dependencies
- Record chain depth

### Step 2: Composition Verification (via chain_verifier_recipe)
Verify the target skill's composition is self-consistent:
- All referenced skills are present
- Pipeline stages are ordered correctly
- No circular dependencies
- Composition complexity matches claimed rarity

### Step 3: Rarity Guard Check (via rarity_guard_lens)
Apply rarity thresholds to verify the skill's claimed rarity:
- Count total dependencies (Z)
- Apply thresholds: Common=Z0, Uncommon=Z1, Rare=Z2+, Epic=emergent
- Flag any inflation vs. actual composition

## Usage
1. Identify target skill (a crafted .md file)
2. Run dependency_audit_recipe → get dependency list
3. Run chain_verifier_recipe → verify composition chain
4. Run rarity_guard_lens → verify rarity alignment
5. Output: verdict + recommendations

## Composition Proof
- Step 1 uses dependency_audit_recipe (loadout)
- Step 2 uses chain_verifier_recipe (loadout)
- Step 3 uses rarity_guard_lens (loadout)
- Total: 3 loadout skills composed into one pipeline
- Rarity: rare (2+ components → rare threshold)

## Test Case
Input: a crafted skill with 2 dependencies and claimed rarity "epic"
- Step 1 finds 2 dependencies (Z=2)
- Step 2 confirms both exist and are valid
- Step 3 applies rarity_guard thresholds: Z=2 → "rare" not "epic"
- Verdict: inflation detected, recommend downgrade to rare

## Why Rare
Three distinct loadout skills are composed into one coherent pipeline, creating emergent capability beyond any single component. The supply-chain verification function doesn't exist in any individual skill — it emerges from the composition.
