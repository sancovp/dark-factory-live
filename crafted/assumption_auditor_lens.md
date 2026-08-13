# Assumption Auditor Lens

**Type:** lens  
**Rarity:** uncommon

## Purpose
Reframes any claim or decision by systematically surfacing, challenging, and testing its hidden assumptions. Assumptions are the load-bearing walls of reasoning — a lens that exposes them changes what you believe is possible.

## Method

### Step 1 — Surface the Assumptions
For any claim or decision under consideration, ask:
- What must be true for this to hold?
- What am I assuming about the actors, the environment, the data, the timeline?
- What would make this claim collapse if false?

List 3–7 explicit assumptions.

### Step 2 — Classify Each Assumption
- **Core:** If this is false, the claim is fatally broken
- **Structural:** The claim holds but looks different if this is false
- **Peripheral:** The claim barely changes if this is false

### Step 3 — Test the Cores First
For each **Core** assumption:
1. State the inverse
2. Find evidence or a case where the inverse held
3. Assign a confidence score (0–1)

### Step 4 — Reframe the Decision
Replace the original claim with: "Given that [Core assumptions] are true, I conclude [X]. If [Core assumption Y] is false, I would need to [revise action]."

## Example
**Claim:** "We should hire more engineers to ship faster."
- Assumption (Core): Team coordination overhead scales sublinearly with headcount
- Assumption (Structural): Engineers are the bottleneck, not process or decisions
- Assumption (Peripheral): Market supply of skilled engineers is adequate
- Test: Many high-performing small teams (3–7) outperform large teams on velocity
- Reframe: Hire if coordination cost is low AND the bottleneck is truly engineering capacity; otherwise fix process first.

## Composition
Works well as input to:
- `divergence-analyzer-recipe` — the adversarial lens sharpens challenge of surfaced assumptions
- `second-order-lens` — second-order effects often live inside core assumptions
- `causation_lens` — assumptions about causal direction are common core failures

## Quality Gate
The lens passes if it surfaces at least 2 core assumptions from any input claim, and at least one core assumption is genuinely non-obvious to the claim-maker.