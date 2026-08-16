# Dependency Impact Assessment Recipe

**Type:** Recipe
**Rarity:** Rare
**Composes:** dependency_trace_lens, rarity_guard_lens

## Purpose
Assesses how a skill dependency chain affects quality and rarity.

## Pipeline Steps

### Step 1: Trace Dependencies
Use dependency_trace_lens in "both" mode.
Count Z = number of present backward dependencies.

### Step 2: Rarity Calibration
Apply rarity_guard_lens thresholds.
Z=0 to Common, Z=1-2 to Uncommon, Z=2+ to Rare.

### Step 3: Impact Score
dependency_weight = Z / (Z + 1)
autonomy_score = 1 - dependency_weight

## Input
{"skill_path": "<path>"}

## Output
{"dependency_count": Z, "calibrated_rarity": "...", "inflation_risk": "..."}

## Composition Proof
dependency_trace_lens + rarity_guard_lens = Rare recipe
