# Threat Model Report — patch-4 Loadout & Quests

**Applied:** Threat Model Lens  
**Date:** 2026-08-14  
**Target:** quests/ + loadout/

---

## CRITICAL: Loadout Skills with Phantom Dependencies

### Attack Surface 1: Recipe Composition References
**File:** `loadout/chain_verifier_recipe.md`  
**References:** `Divergence Lens`, `Convergence Lens`  
**Status:** ❌ MISSING from loadout

**File:** `loadout/inversion_second_order_recipe.md`  
**References:** `constraint_inversion_lens.md`, `second_order_lens.md`  
**Status:** ❌ MISSING from loadout

### Failure Modes
| Failure | Severity | Likelihood | Priority |
|---------|----------|------------|----------|
| Recipes fail at runtime (missing ingredients) | 5 | 5 | **25** |
| Players boot with non-functional loadout | 5 | 5 | **25** |
| Trust violation (claims don't match reality) | 4 | 4 | **16** |

### Mitigation
Install referenced skills to loadout OR rewrite recipes to use available skills.

---

## HIGH: Quest Reward Rigidity
### Attack Surface 2: Hardcoded Rewards
**File:** `quests/q_forge_lens.md` → 60 gold  
**File:** `quests/q_recipe_chain.md` → 120 gold

**Failure Mode:** Rewards not indexed to market conditions; early-game players may exploit low-risk/high-reward quests.

### Mitigation
Consider dynamic reward scaling based on quest difficulty or market average.

---

## MEDIUM: Test Record Unverifiability
**Surface:** `.tests/*.json` files are plain JSON, easily fabricated.

**Failure Mode:** Fake test records could be created to bypass gate checks.

**Priority:** 3 × 3 = **9**

---

## Summary

| Priority | Issue | File |
|----------|-------|------|
| **CRITICAL** | Phantom dependencies in recipes | loadout/*.md |
| HIGH | Reward rigidity | quests/*.md |
| MEDIUM | Unverifiable test artifacts | crafted/.tests/ |

**Recommended Action:** Fix phantom dependencies before loadout ships.
