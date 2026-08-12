# Lens: Stakeholder Symmetry
Type: Lens
Rarity: Uncommon

## Description
Reframes problems by examining them from the perspective of ALL stakeholders, including adversarial ones. Every system has multiple actors with different incentives — this lens forces you to think from each position simultaneously.

## The Questions
When examining any decision, system, or problem, ask for each stakeholder:

1. **What does this stakeholder WANT?** (stated goal)
2. **What does this stakeholder INCENTIVIZE?** (real behavior driver)
3. **What would this stakeholder DO to maximize their incentive?** (potential action)
4. **How does this stakeholder's action CONFLICT with others?** (tension point)

## Application
For ANY proposed change, generate the Stakeholder Matrix:

| Stakeholder | Wants | Incentivized To | Will Do | Conflicts With |
|-------------|-------|-----------------|---------|----------------|
| A | X | Y | Z | W |
| B | ... | ... | ... | ... |

## Output Shape
- **Stakeholder Map**: Who has power, who has interest
- **Tension Points**: Where incentives misalign
- **Design Constraints**: What the conflicts force you to build around
- **Hidden Beneficiaries**: Who gains without wanting it

## When to Apply
- Before making architectural decisions
- When evaluating others' proposals
- During code review (who does this help? who does it hurt?)
- At the START of analysis, not after

## Example Transformation
**Before Stakeholder Symmetry:**
"Add admin panel for easier content management"

**After Stakeholder Symmetry:**
| Stakeholder | Wants | Incentivized To | Will Do | Conflicts With |
|-------------|-------|-----------------|---------|----------------|
| Admins | Control | More access | Create nested permissions | Security team |
| Users | Privacy | Hide data | Use VPNs/alt accounts | Admins |
| Attackers | Access | Exploit trust | Phishing admins | Both |

Design constraint: **admin panel must not create asymmetric trust** (admin account compromise = user data loss)

## Quality Indicator
If all stakeholders agree something is good, you're probably missing a stakeholder or mischaracterizing incentives. Genuine disagreement reveals real tension.
