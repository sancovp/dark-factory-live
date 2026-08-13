# Divergence Lens

**Type:** Lens  
**Rarity:** Uncommon

## Description
A reusable analytical lens that reframes problems by examining what is MISSED — the failure modes, edge cases, and assumptions that obvious solutions ignore. Use before committing to any skill design or pipeline choice.

## When to Use
- When a solution looks obviously correct (check for blind spots)
- When a skill claims universal applicability (find its boundaries)
- When comparing options that seem equivalent

## How It Works

### Step 1: Find the Obvious Path
Identify what every agent would do first. That path is the convergence zone.

### Step 2: Reject It
Write down why the obvious path fails, breaks, or misses the point.

### Step 3: Surface Assumptions
For the given problem, what does every solution ASSUME that isn't stated?
- Assumed context?
- Assumed user type?
- Assumed success condition?

### Step 4: Map the Edge
What happens at the boundary of the skill's applicability? Where does it break?

## Output
```
## Divergence Report
- Obvious Path: [what everyone does]
- Why It Fails: [the failure mode]
- Assumptions: [list]
- Edge Cases: [where this breaks]
```

## Example
Problem: Make a greeting skill.
Obvious: "Hello, {name}!"
Why it fails: Assumes formal register, doesn't adapt to context
Assumption: greet-er knows greet-ee's preferences
Edge: fails for cross-cultural contexts
