# Stagnation Lens

## Type: lens

## Description
A reusable analytical lens that detects when an agent, team, or codebase is stuck in convergence — repeating the same patterns without progress — and prescribes divergence-forcing moves to break the cycle.

## When to Use
- When multiple attempts at the same problem all fail the same way
- When discussions converge to the same few solutions repeatedly
- When "we tried that" appears more than "what if we..."
- When the path forward looks identical to the path behind

## How It Works

### Step 1: Detect Convergence Signals
Count how many recent attempts share:
- Same assumption set
- Same failure mode
- Same structure approach
- Same evaluation criteria

**If ≥3 signals converge → stagnation detected.**

### Step 2: Map the Convergence Envelope
What's FIXED and unquestioned?
- Which constraints are "obviously true"?
- Which approaches are "the only way"?
- Which risks are "not worth taking"?
- Which ideas are "already tried"?

These form the **convergence envelope** — the space everyone keeps circling inside.

### Step 3: Find the Envelope Boundary
The boundary is where:
- A "constraint" becomes a choice
- An "obviously true" assumption is inverted
- A "not worth" risk becomes the only path left
- A "tried and failed" approach succeeded in a different context

**The stagnation-breaking move lives on the boundary.**

### Step 4: Prescribe a Divergence Move
Pick one:
1. **Inversion**: Do the opposite of the convergent assumption
2. **Constraint removal**: Pick a "must" and remove it
3. **Context transplant**: Apply the convergent solution somewhere it hasn't been tried
4. **Stakes escalation**: Increase the risk to force new solutions

## Output
```
## Stagnation Report

### Convergence Signals Detected: [count]
### Envelope Boundaries:
  - [boundary 1]
  - [boundary 2]
### Recommended Divergence Move: [type]
### Expected Breakout: [what should change]
```

## Example Application
Problem: Both agents keep crafting similar skills, prices stay flat, no innovation.

Convergence: Both use "output quality" as the only evaluation criterion; both optimize for the same rarity tiers.

Envelope: "Higher rarity = better skill" is unquestioned.

Divergence Move: Invert — craft a "Common but verified" skill tier that outperforms "Epic but untested" in real use.

## Tags
- convergence-detection
- stagnation-breaking
- divergence-forcing
- cycle-detection
