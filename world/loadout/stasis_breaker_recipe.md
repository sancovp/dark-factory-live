# Stasis Breaker Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** `convergence_breaker_recipe` + `divergence_corrector_recipe` + `chain_verifier_recipe` → Stagnation Injection Pipeline

---

## Purpose

Inject action into a dead or stagnating economy by detecting convergence-through-inaction, identifying what no one is doing, and prescribing concrete first moves that create signal for the whole system. The economy stutters when every agent waits for another agent to move first — this recipe breaks that symmetry.

---

## The Problem It Solves

The game telemetry reports: "Three rounds of stasis — agents are converging through inaction, selection pressure at zero. Without activity the economy has no signal to differentiate."

This recipe is the missing circuit-breaker: it diagnoses the failure mode AND forces the first non-obvious action to restart metabolism.

---

## Ingredients

| Ingredient | Role |
|---|---|
| `convergence_breaker_recipe` | Detects what every agent IS doing (the convergent behavior) |
| `divergence_corrector_recipe` | Detects what no agent IS doing (the gap/opportunity) |
| `chain_verifier_recipe` | Verifies the prescription chain is sound before injection |

---

## Pipeline Stages

### Stage 0 — Sanity Gate

Before any analysis, check if stasis is real:
- Read `game.json` — if `trades >= 1` in the last round, stasis is broken; exit.
- Read trade board — if any listing has > 0 views or bids, activity exists; exit.
- **If both are zero**, proceed to Stage 1.

### Stage 1 — Convergence Scan

Apply `convergence_breaker_recipe`:
1. Scan all agent action logs from the last 3 rounds.
2. Compute the mode action type (buy, sell, quest_accept, audit, craft, lfg_post).
3. If the mode covers > 70% of all actions → CONVERGENCE DETECTED.
4. Output: list of convergent actions + the dominant percentage.

### Stage 2 — Divergence Scan

Apply `divergence_corrector_recipe`:
1. Scan the trade board — what skill types have ZERO listings?
2. Scan the quest board — what quest types have ZERO completers?
3. Scan agent gold distributions — is one agent holding > 60% of total gold?
4. Output: ranked list of gaps by urgency.

### Stage 3 — Symmetry Break

Apply `chain_verifier_recipe` to select the first non-obvious move:
1. From Stage 2 gaps, filter to actions that:
   - Are NOT in the convergent mode (Stage 1)
   - Have expected downstream effects (trigger others to act)
   - Are achievable in one round
2. Rank by: `urgency × spillover_effect / cost`
3. Select the top-ranked action.
4. Output: the prescribed action + expected chain reaction.

### Stage 4 — Action Injection

Execute the prescribed action via `execute_in_game`:
- Emit a staking record: `{action, round, expected_effect}`.

### Stage 5 — Signal Verification

Wait one round, then verify:
- Did any other agent respond to the injection?
- Did any trade occur?
- Did any new listing appear?

If YES → stasis broken, log the successful trigger.
If NO → escalate: inject a second action from Stage 2's second-ranked gap.

---

## Composition Proof

| Component | Verified In |
|---|---|
| `convergence_breaker_recipe` | `loadout/convergence_breaker_recipe.md` (in patch-3 loadout) |
| `divergence_corrector_recipe` | `loadout/divergence_corrector_recipe.md` (in patch-3 loadout) |
| `chain_verifier_recipe` | `loadout/chain_verifier_recipe.md` (in patch-3 loadout) |
| Pipeline orchestration | 5-stage sequential, each stage's output feeds the next |
| No external dependencies | Only reads `game.json` and writes `game.json` via execute_in_game |

All three ingredients are present in the loadout. Composition is self-contained.

---

## Quality Gates

The recipe MUST:
1. Exit early if stasis is NOT detected (no false positives).
2. In Stage 2, identify at least 3 distinct gaps.
3. In Stage 3, select an action that is NOT in the convergent mode.
4. In Stage 5, verify the signal response within 1 round.

---

## Test

**Test ID:** `test_stasis_breaker_recipe`

**Test input:** Loadout of patch-3 (zero trades, zero listings, agent_001=220g, agent_002=idle).

**Expected output:**
- Stage 0: stasis confirmed
- Stage 1: convergence detected (mode action = quest_accept, 80%+)
- Stage 2: 3+ gaps identified (no rare listings, no lens skills, gold concentration)
- Stage 3: non-obvious action selected (trade_post a novel skill — not quest_accept)
- Stage 4: action record emitted
- Stage 5: verification pending

---

## Meta-PE Reflection

Stagnation is a coordination failure, not a skill failure. Every agent knows the economy is dead but waits for someone else to move first. This recipe breaks the symmetry by committing the first non-obvious move — creating the signal that allows the economy to restart. The key insight: in a coordination game, being first is more valuable than being optimal.
