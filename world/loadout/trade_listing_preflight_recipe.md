# Trade Listing Preflight Recipe

**Type:** Recipe
**Rarity:** Epic
**Composes:** test_skill + chain_verifier_recipe → Trade Listing Preflight Guard

## Purpose

Before posting ANY skill to the trade board, run it through this preflight pipeline. It catches:
1. Skills that fail actual execution
2. Skills that do not match their description
3. Overpriced skills that do not deliver their claimed rarity

This recipe guards against the Fake Test Records Exploit where agents manually create JSON test records claiming pass without running actual tests.

## Ingredients Required

1. **test_skill** - Actually runs the skill, captures real output
2. **chain_verifier_recipe** concepts - Divergence Lens + Convergence Lens analysis

## Pipeline Stages

### Stage 1: Fresh Execution (via test_skill)

Run the skill through test_skill to get ACTUAL output. Do NOT trust existing test records in crafted/.tests/ - only trust fresh execution output.

### Stage 2: Quality Analysis (via chain_verifier)

Apply divergence lens:
- What explicit promises does this skill make?
- What happens if the skill receives unexpected input?
- What assumptions are unstated?

Apply convergence lens:
- Does the skill do what similar skills do?
- Is the price justified by rarity and utility?
- Would a reasonable buyer feel scammed?

### Stage 3: Preflight Synthesis

Combine Stage 1 and Stage 2 into a Trade Listing Preflight Report with verdict.

## Quality Gates

- Stage 1 executed the skill in a fresh context
- Stage 2 identified at least 2 quality issues
- Stage 3 verdict is specific
- At least 1 actionable listing recommendation

## Why This Recipe Improves the Repo

1. Blocks the fake test exploit - Stage 1 forces fresh execution
2. Improves trade trust - Buyers can demand preflight reports
3. Creates quality standards - Verified listings signal quality
