---
name: loadout_readiness_lens
description: Reframes skill analysis to evaluate whether a skill can safely enter loadout — checking composition, dependencies, and gate survival probability.
type: lens
rarity: uncommon
---

# Loadout Readiness Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Reframe skill evaluation to focus on loadout admission safety

## How to Use

When examining any skill for loadout admission, shift perspective from "what does this skill do?" to "can this skill survive the gate and safely enter loadout?"

## The Loadout Readiness Frame

### Step 1: Dependency Check
Ask: "Does this skill reference components that exist in loadout?"
- Parse all import/reference statements
- Verify each dependency exists
- If ANY dependency is missing → NOT loadout-ready

### Step 2: Composition Proof
Ask: "If this skill composes other skills, has the composition been proven?"
- Check for test records
- Verify composition chain is unbroken
- If composition unverified → NOT loadout-ready

### Step 3: Gate Survival Probability
Ask: "What is the probability this skill passes the gate test?"
- Check against audit_valid_not_gate_valid rule
- Surface-level validation ≠ gate survival
- If only surface validation exists → MEDIUM risk

### Step 4: Loadout Collision
Ask: "Does this skill conflict with any existing loadout component?"
- Check for duplicate functionality
- Check for opposing directives
- If collision exists → NOT loadout-ready without resolution

## Output

For any skill under evaluation, produce:
```
Loadout Readiness Report
========================
Dependency Status: [SAFE/GAP]
Composition Proof: [VERIFIED/UNVERIFIED]  
Gate Survival Prob: [HIGH/MEDIUM/LOW]
Collision Status: [CLEAR/COLLISION]
FINAL VERDICT: [READY/NOT READY]
```

## Example Application

Input: dependency_proof_recipe.md
- Dependencies: dependency_lens ✓, test_skill ✓
- Composition: two-stage pipeline ✓
- Test record: exists ✓
- Collision: none detected ✓
→ VERDICT: LOADOUT READY

## Quality Gate

A lens application must:
- Cover all 4 dimensions (deps, composition, gate, collision)
- Report specific gaps if NOT READY
- Provide actionable next steps
