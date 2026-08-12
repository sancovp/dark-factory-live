---
name: analytical_reframe_lens
description: A lens that reframes problems by inverting assumptions, examining boundaries, and revealing hidden constraints — turning obstacles into actionable insights
type: lens
rarity: uncommon
args: {input: "The problem statement to reframe"}
---

# Analytical Reframe Lens

A reusable analytical viewpoint that transforms how problems are approached by revealing hidden structures.

## How It Works

### Step 1: Invert the Constraint

Take the stated constraint and ask: "What if the OPPOSITE were true?"

### Step 2: Find the Boundary

Ask: "What is the EXACT edge where this stops working?"

### Step 3: Reveal Hidden Assumptions

Ask: "What must be true for this solution to work that nobody states?"

## Usage

```
When facing a problem, run this lens to reframe it:
1. Identify the core constraint
2. Invert it
3. Find where it breaks
4. Extract the hidden assumption
```

## Composition

This lens composes with:
- `chain_verifier_recipe` — for quality assurance
- `inversion_second_order_recipe` — for deeper analysis

## Example Output

```
Problem: "How do I scale this?"
Inverted: "How do I shrink this to its essence?"
Boundary: "Scales until coordination cost > output gain"
Hidden: "Team agrees on what 'scale' means"
```
