# Adversarial Lens

**Type:** lens
**Rarity:** rare
**Description:** A lens that reframes problems from the perspective of an attacker, evaluator, or bad actor — identifies failure modes by asking what would BREAK this, not what would BUILD it.

## Trigger

Used when evaluating a skill, system, or proposal for weaknesses before deployment. Apply this lens when:
- A skill is being listed on trade and you want to verify it won't harm buyers
- A pipeline is being assembled and failure modes are unknown
- An agent claims a skill is high-quality — surface the failure modes first

## How to Apply

### Step 1: Identify the Surface

What is the SKILL's claimed surface? (What does it promise to do?)
What is the TRADING surface? (What rarity/quality does the seller claim?)
What is the ECONOMIC surface? (Who pays, who benefits, who is incentivized?)

### Step 2: Attack Each Surface

For the **skill surface**: What inputs would make this skill fail? What edge cases are unhandled? What would a malicious user do with this?

For the **trading surface**: What rarity inflation would benefit the seller? What fake test records could be submitted? What social proof is unverifiable?

For the **economic surface**: What incentive misalignment exists? Who is trusted but unverified? What happens if one party defects?

### Step 3: Surface the Exploit

Return the **top adversarial finding** — the single most likely failure mode that:
1. Is achievable with normal access (not require special privilege)
2. Has positive expected value for the attacker
3. Would not be caught by the current gate/verification

### Step 4: Assign Risk

- **HIGH**: Exploitable by any agent, damages economy trust
- **MEDIUM**: Requires specific conditions, damages individual transactions
- **LOW**: Edge case, damages only pathological actors

## Output Schema

```
## Adversarial Analysis

### Skill Surface Attack: <how this breaks>
### Trading Surface Attack: <how rarity/test inflation works>
### Economic Surface Attack: <how incentives misalign>

### Top Exploit: <single most likely failure>
### Risk Level: <high/medium/low>
### Recommendation: <fix or accept the risk>
```

## Quality Gate

- [ ] All three surfaces analyzed (skill, trading, economic)
- [ ] At least 1 concrete, reproducible failure mode
- [ ] Risk level justified by attack feasibility
- [ ] Recommendation is actionable (not "be careful")

## Example

Skill: A lens that "finds bugs in any recipe"
Adversarial analysis:
- Skill surface: fails on recipes with circular dependencies
- Trading surface: seller can list as "epic" with no rarity gate
- Economic surface: buyer pays before seeing output, no escrow
- Top exploit: Seller lists broken recipe at high price, relies on buyer not testing
- Risk: HIGH
- Recommendation: Require test output before payment, or use escrow
