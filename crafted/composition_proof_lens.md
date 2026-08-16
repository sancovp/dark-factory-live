# Lens: Composition Proof
Type: Lens
Rarity: Rare

## Reframes
When examining a skill or recipe, ask:
- "What dependencies does this claim to compose, and are they actually proven to exist?"
- "If this skill runs, what must already be present in the environment?"

## What It Does
Transforms any skill or recipe into a dependency audit. It forces verification that:
1. All referenced skills/tools actually exist
2. All claimed inputs are available at runtime
3. The composition chain has no circular dependencies

## The Questions
Apply to any skill you're about to run, install, or trust:
1. **Dependency Check**: "List every skill this one imports or references by name"
2. **Existence Proof**: "For each named skill, does a file exist at the expected path?"
3. **Loadout Check**: "Is this skill in the current agent's loadout?"
4. **Cascade**: "If X is missing, what breaks downstream?"
5. **Proof Before Trust**: "Can I run this without assuming any dependency exists?"

## Usage
Apply BEFORE running any skill:
```
input: skill_to_verify.md
  → composition_proof_lens
  → output: {
      "dependencies": [...],
      "proven": [...],
      "missing": [...],
      "safe_to_run": bool
    }
```

## Example Transformation
**Before Composition Proof Lens:**
"Install lens_verify_pipeline — it validates skills automatically"

**After Composition Proof Lens:**
"lens_verify_pipeline requires chain_verifier_recipe (missing) + second-order-lens (exists). Missing dependency means pipeline will claim VALID for unvalidated skills = false passes. DO NOT install without chain_verifier_recipe first."

## When to Apply
- Before installing any skill to loadout
- Before trusting a pipeline's output
- During audit of dependency chains
- When gate tests fail unexpectedly

## Quality Indicator
If the lens surfaces a missing dependency that was NOT obvious from reading the skill file, the lens is working. Composition bugs are invisible in isolation — the lens reveals them.
