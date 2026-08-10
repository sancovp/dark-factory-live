# Skill: Convergence Divergence Lens

## Type: lens

## Description
Identifies whether a system, idea, or pattern is converging toward stability or diverging toward instability, and what forces drive each trajectory.

## The Core Questions
1. **What is the current trajectory?** — Converging or diverging from a reference point?
2. **What forces accelerate convergence?** — Feedback loops, penalties, selection pressure
3. **What forces accelerate divergence?** — Mutations, noise, external perturbations
4. **What is the basin of attraction?** — Where does convergence stabilize?
5. **What breaks convergence?** — The perturbation threshold that flips to divergence

## Analytical Framework

### Convergent Indicators
- Selection pressure increasing over time
- Variance decreasing in outcomes
- Actors behaving more similarly
- Information bottlenecks forming
- Reward gradients flattening

### Divergent Indicators  
- Exploration rate increasing
- Variance expanding
- Novel combinations emerging
- Roles/specializations proliferating
- Selection pressure weakening or inconsistent

## Application
Apply to any system where you ask: "Is this becoming more similar over time (converging) or more varied (diverging)?"

### Step 1: Baseline
Establish the reference state — what counts as "same" vs "different"?

### Step 2: Measure Trajectory
Apply both lens sides:
- Convergent side: what pushes toward the center?
- Divergent side: what pushes toward the edges?

### Step 3: Identify Drivers
Map the forces explicitly. Most systems have BOTH operating simultaneously.

### Step 4: Find the Tipping Point
What parameter value flips convergence → divergence or vice versa?

## Output Shape
{
  "trajectory": "converging" | "diverging" | "oscillating" | "stable",
  "convergence_forces": [...],
  "divergence_forces": [...],
  "tipping_point": "description of threshold",
  "implications": "what this trajectory means for the system's future"
}

## Rarity: rare

## Input Triggers
- "Are agents behaving the same?"
- "Is the market consolidating?"
- "Are ideas converging?"
- "Is this design space being explored or exhausted?"
