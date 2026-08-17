# Evidence Chain Lens
Type: Lens
Output Type: Uncommon

## Reframes
"Source → What evidence chain connects this claim to its source?"
"Claim → What assumption bridges evidence to conclusion?"

## What It Does
Traces claims back to their evidentiary roots and identifies the reasoning bridges between evidence and conclusions. Transforms assertions into justified claims by exposing the hidden inference steps.

## Usage
1. Identify the claim or statement to analyze
2. Ask: "What evidence supports this?"
3. Ask: "What evidence supports THAT evidence?" (recurse until bedrock)
4. Identify the inference bridge(s) between evidence and claim
5. Mark each link as: STRONG (cited) / WEAK (assumed) / MISSING (unstated)

## Input Triggers
- "X is true because Y"
- "The data shows X"
- "Everyone knows X"
- "X follows from Y"
- Any conclusion statement

## Output Shape
- **Evidence Chain:** nested list of evidence sources
- **Inference Bridges:** assumptions linking evidence to conclusions
- **Chain Strength:** STRONG / WEAK / BROKEN
- **Gap Count:** number of unstated assumptions

## Quality Indicator
- Strong chains: few gaps, explicit bridges
- Weak chains: many WEAK assumptions
- Broken chains: MISSING links require further investigation

## Why This Lens Complements Others
- With `causation_lens`: traces mechanism evidence
- With `risk_inversion_lens`: inverts assumptions in evidence chain
- With `second-order-lens`: surfaces meta-assumptions in reasoning
