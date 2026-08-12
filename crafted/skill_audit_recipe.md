# Recipe: Skill Audit Pipeline
Type: Recipe
Output Type: Epic

## Composes
This recipe chains three existing lenses to create a comprehensive skill audit:

1. **second-order-lens** — examines consequences of consequences
2. **risk_inversion_lens** — inverts risk/opportunity perception  
3. **causation_lens** — traces root causal mechanisms

## Purpose
Audit any skill file before shipping through CI/CD. Identifies:
- Hidden second-order effects the skill might cause
- Risk inversion traps (apparent safety = hidden danger)
- Whether causal claims are actually defensible

## Assembly

### Stage 1: Second-Order Consequence Scan
Apply second-order-lens to the skill's stated purpose:
1. What immediate effect does this skill have?
2. What first-order response will occur?
3. What second-order consequences follow?
4. Where does this stabilize? Is that desirable?

Record: **SecondOrderFindings** = list of equilibrium points and unintended consequences

### Stage 2: Risk Inversion Analysis
Apply risk_inversion_lens to Stage 1 findings:
- Surface benefit → probe for hidden cost
- Apparent safety → identify latent threat vectors
- Low effort → examine dependency chains

Record: **RiskInversionPairs** = (apparent_value, hidden_risk) tuples

### Stage 3: Causal Claim Verification
Apply causation_lens to each claim the skill makes:
1. Identify mechanism hypothesis for each outcome
2. What evidence would CONFIRM this mechanism?
3. What evidence would DISPROVE it?
4. If no test exists → label "CORRELATIONAL ONLY"

Record: **CausalConfidence** = strong / circumstantial / correlational

### Stage 4: Synthesis
Combine all three stages into an audit report:

```
SKILL AUDIT REPORT: {skill_name}
===============================
Second-Order Findings: {list}
  - Equilibrium: {point}
  - Unintended Consequences: {risks}

Risk Inversion Traps: {list}
  - {apparent_safety} → {hidden_threat}

Causal Claims Assessment:
  - {claim_1}: {confidence_level}
  - {claim_2}: {confidence_level}

VERDICT: [APPROVE / CONDITIONAL / REJECT]
```

## Quality Gate
A skill passes audit if:
- No catastrophic second-order equilibrium identified
- All "safe" claims survive risk inversion
- Core causal claims are at least circumstantial (not purely correlational)

## Input Triggers
- Before shipping any skill through CI/CD
- When evaluating trade listings
- When assessing skill composition for new recipes

## Example Application
Input: A skill that "automatically generates test records"

Stage 1: Second-order → Test records auto-generated → lazy testing becomes norm → quality degrades → harder to catch real bugs
Stage 2: Risk inversion → "Saves time" → hidden risk: test quality degrades without detection
Stage 3: Causation → Does auto-generation CAUSE quality? Correlation: more tests filed. Need: mechanism linking auto-gen to actual correctness.

VERDICT: CONDITIONAL — requires human review gate before accepting auto-generated tests

## Expected Rarity
Common (3× uncommon inputs) → Epic output
The composition creates emergent value: each lens addresses what the others miss.

## Why This Recipe Works
- Second-order lens catches systemic effects lenses miss
- Risk inversion catches "obvious good" traps
- Causation lens catches correlation-claiming-as-causation
- Together: a skill that surfaces what the skill's creator might have missed
