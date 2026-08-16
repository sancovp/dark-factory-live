# Constraint Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Identify which constraints in a problem/skill are essential vs. arbitrary — reframes what "must" be true

## The Problem

Every skill makes assumptions. Every problem statement contains embedded constraints. Most agents accept these constraints without questioning them, producing skills that solve the stated problem but miss the real problem underneath.

The Constraint Lens forces you to ask: "What would break if this constraint disappeared?"

## How It Works

Apply this lens to ANY skill or problem statement. For each constraint you find, classify it:

### Constraint Types

| Type | Description | Question |
|------|-------------|----------|
| **Essential** | Removing it breaks the core purpose | "Does the skill fail if this goes away?" |
| **Traditional** | No longer necessary, kept by habit | "Has this constraint outlived its reason?" |
| **Arbitrary** | Could be anything, happens to be this | "Is this value/format genuinely needed?" |
| **Imposed** | External requirement, not intrinsic | "Who decided this and why?" |

## Application Protocol

### Step 1: Extract Constraints

Read the skill/problem and list every constraint you can find:
- "Must use X format"
- "Cannot exceed Y length"
- "Requires Z as input"
- "Only works when W is true"

### Step 2: Challenge Each

For each constraint, ask:
1. **What would happen if this constraint were REMOVED?**
2. **What would happen if this constraint were RELAXED?**
3. **What would happen if this constraint were INVERTED?**

### Step 3: Classify

After challenging:
- If removal breaks core purpose → **Essential** (keep it, make it explicit)
- If removal improves outcome → **Traditional** or **Arbitrary** (question it)
- If removal is impossible due to external factors → **Imposed** (document why)

### Step 4: Reframe

Create a reframed version of the skill/problem:
```
## Original Problem
[the stated problem with embedded constraints]

## Essential Constraints
- [only the truly necessary ones]

## Removable Constraints  
- [constraints that could be relaxed or removed]

## Reframed Problem
[the problem WITHOUT the removable constraints]
```

## Example

**Input:** "Write a function that sorts a list of integers in ascending order"

**Constraint Analysis:**
- "sorts" → Essential (the core purpose)
- "integers" → Traditional? Numbers could be floats or strings
- "ascending" → Could be descending, or unsorted visualization
- "list" → Could be stream, array, or generator

**Reframed Problem:** "Transform a sequence of comparable values into ordered output"

## When to Use

- Before crafting a skill: Does your problem statement have hidden constraints?
- During skill review: Are the skill's constraints intentional or inherited?
- When stuck: Try removing constraints to find a simpler solution
- Challenge phase: Apply before other lenses to expose the real problem

## Why This Lens Improves the Repo

1. **Prevents cargo-culting:** Skills that inherit constraints from training data or templates often contain obsolete requirements.
2. **Finds the real problem:** The stated problem is often not the interesting problem.
3. **Enables innovation:** Most breakthroughs come from removing "obvious" constraints.
4. **Composes with other lenses:** Run Constraint Lens FIRST, then apply other lenses to the reframed problem.

## Quality Check

A Constraint Lens analysis is complete when:
- At least 5 constraints are identified
- Each constraint is classified (Essential/Traditional/Arbitrary/Imposed)
- At least 2 constraints are flagged as Traditional or Arbitrary
- A reframed problem is produced that differs from the original

## Rarity Justification

Uncommon — single lens, novel analytical framework, composes with any skill type.
