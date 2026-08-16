# Recipe: Convergence Pressure Analyzer
Type: Recipe
Output Type: Epic

## Composes
1. **causation_lens.md** — identifies causal mechanisms from correlational patterns
2. **second-order-lens.md** — traces consequences-of-consequences
3. **risk_inversion_lens.md** — inverts surface risk into hidden opportunity and vice versa

## Assembly (three-pass pipeline)

### Pass 1 — Causation (what made this happen?)
Apply `causation_lens` to the raw input:
- "What causal mechanism could produce this pattern?"
- "Why now — what changed?"
Output: Mechanism hypothesis + evidence required + disproof test + confidence tier.

### Pass 2 — Second-Order (what happens next?)
Take Pass 1's mechanism and apply `second-order-lens`:
- "Immediate effect of this mechanism?"
- "First-order responses from people/systems?"
- "Second-order responses to those reactions?"
- "Equilibrium — where does it stabilize? Is that desirable?"
Output: Causal chain with depth-2 consequence tree.

### Pass 3 — Risk Inversion (what are we blind to?)
Take the full Pass 2 analysis and apply `risk_inversion_lens`:
- Invert each apparent risk → probe hidden opportunity
- Invert each apparent safety → probe latent threat
- Surface dependency chains and single points of failure
Output: Risk/opportunity pairs with asymmetry analysis.

### Synthesis
Combine into a single output with three sections:
1. **Causal Hypothesis** (from Pass 1)
2. **Consequence Tree** (from Pass 2)
3. **Inverted Risk Map** (from Pass 3)
Close with: "What single intervention changes the most edges in the tree?"

## Quality Gates
- Pass 1 must produce a mechanism hypothesis (not just a restatement)
- Pass 2 must reach at least depth-2 (second-order), not just first-order
- Pass 3 must flip at least one "safe" assumption into a hidden threat
- All three lenses must be active — removing any one degrades the output
- Final synthesis must name a concrete intervention, not abstract advice

## Expected Rarity
Three-ingredient pipeline where each lens covers a distinct failure mode
(correlation-blindness, shallow analysis, risk misperception) → Epic output.
The combination is strictly more powerful than any single lens.

## Why This Recipe Works
Single lenses miss two of three failure modes. Causation alone stops at
"why"; second-order alone stops at "so what"; risk-inversion alone is
directionless. Chaining all three forces: identify the cause, trace its
ripple, then ask which ripple you can still intercept — producing an
actionable intervention, not just an analysis.
