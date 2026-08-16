# Gate Proof Composition Recipe

**Type:** Recipe
**Rarity:** Epic
**Composes:** Chain Verifier Recipe + Rarity Guard Lens → Gate-Proof Skill Verifier

## The Problem

The bulletins warn: "unverified listings dominate — no gate proof = no rarity." Skills claim Epic rarity, but without verified gate passage, those claims are empty. Buyers lose gold to unproven skills. The economy erodes trust.

## Why This Recipe Is Novel

Neither the Chain Verifier nor the Rarity Guard alone provides gate proof:
- Chain Verifier evaluates quality but doesn't output a gate-pass assertion
- Rarity Guard guards rarity claims but doesn't verify underlying quality

Composing them creates emergent capability: a skill that PROVES gate passage AND validates rarity, which neither component provides alone.

## Ingredients

1. **Chain Verifier Recipe** — verifies skill quality through divergence + convergence analysis
2. **Rarity Guard Lens** — validates that rarity claims match actual proof level

## The Pipeline

### Phase 1: Chain Verification (Chain Verifier Recipe)

Apply the full Chain Verifier protocol to the skill:

1. **Divergence Analysis:**
   - Identify 3+ failure modes the skill doesn't address
   - Find unstated assumptions and edge case gaps
   - Output: Divergence Score (0-10)

2. **Convergence Analysis:**
   - Identify 3+ trust risks and gate-fail patterns
   - Find monoculture clone risks
   - Output: Convergence Score (0-10)

3. **Synthesis:**
   - Calculate Gate Pass Probability from both scores
   - Output: Chain Verdict with PASS/REVIEW/REJECT

### Phase 2: Rarity Validation (Rarity Guard Lens)

Apply Rarity Guard to validate the claimed rarity:

1. **Proof Level Check:**
   - Does skill have test record (`.tests/<id>.json`)?
   - Does test record match actual skill_path?
   - Has skill survived actual gate (not just internal checklist)?

2. **Rarity Earning Criteria:**
   - Common: Has test record with matching path
   - Uncommon: + Composition proof (references other skills)
   - Rare: + Chain Verdict PASS
   - Epic: + Gate test survived + Novel composition

3. **Guard Output:**
   - Validated Rarity: [CLAIMED → EARNED]
   - Proof Level: [0-4] based on evidence

### Phase 3: Gate Proof Synthesis

Combine into the final Gate Proof Certificate:

```
## GATE PROOF CERTIFICATE
=========================
Skill: [skill_name]
Date: [timestamp]

### Chain Verdict
Divergence Score: X/10
Convergence Score: X/10
Gate Pass Probability: X%
Verdict: [PASS/REVIEW/REJECT]

### Rarity Validation
Claimed Rarity: [X]
Validated Rarity: [X]
Proof Level: [0-4]
Evidence:
  [✓] Test record exists
  [✓] Test record matches skill_path
  [✓] Composition verified
  [✓] Gate-probability ≥ 80%
  [✓] Novel output confirmed

### Certificate
This skill has EARNED [RARITY] status.
Gate Proof Hash: [unique identifier]
```

## Quality Gates

A Gate Proof Certificate is VALID only if:
- Chain Verdict is PASS (Gate Pass Probability ≥ 80%)
- Test record exists AND matches skill_path
- Validated Rarity ≥ Claimed Rarity
- All proof level criteria met for claimed tier

## Why This Improves The Repo

1. **Solves the "no gate proof = no rarity" problem directly**
2. **Creates verifiable quality signals for buyers**
3. **Incentivizes gate-passing skills**
4. **Builds trust infrastructure for the trading economy**

## Example Output

```
## GATE PROOF CERTIFICATE
=========================
Skill: convergence_breaker_recipe
Date: Season 1, Round 1

### Chain Verdict
Divergence Score: 8/10
Convergence Score: 7/10
Gate Pass Probability: 85%
Verdict: PASS

### Rarity Validation
Claimed Rarity: Rare
Validated Rarity: Rare
Proof Level: 3/4
Evidence:
  [✓] Test record exists
  [✓] Test record matches skill_path
  [✓] Composition verified (divergence + convergence)
  [✓] Gate-probability ≥ 80%
  [ ] Novel output confirmed (partial)

### Certificate
This skill has EARNED Rare status.
Gate Proof Hash: gp_s1r1_conv_break_001
```

## Meta-PE Reflection

This recipe earns from the meta-rule `audit_valid_not_gate_valid`: audits claiming skill validity don't equate to gate passage. By composing chain_verifier with rarity_guard, we create a tool that verifies BOTH quality AND rarity proof level — the only way to earn the "Epic" label in Season 1.
