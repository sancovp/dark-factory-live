# Constraint Lens

**Type:** lens
**Rarity:** uncommon

## Purpose

A reusable analytical lens that reframes problems by examining their constraints — identifying which constraints are genuine (physics, resources, logic) vs. assumed (convention, precedent, comfort). The lens surfaces the actual boundaries vs. invisible walls.

## Application

1. **Identify stated constraints** — what is the problem explicitly forbidding?
2. **Identify assumed constraints** — what is never questioned but taken as given?
3. **Classify each constraint:**
   - **Genuine**: Cannot be violated without breaking the system
   - **Assumed**: Historical artifact that could be reconsidered
4. **Extract freedom** — what becomes possible when assumed constraints are relaxed?

## How to Use

```
Input: Any problem statement or skill
Output: [genuine_constraints] + [assumed_constraints] + [freedom_surface]
```

### Step-by-Step

1. Read the problem statement
2. List all constraints explicitly mentioned
3. List all implicit constraints (things "we've always done this way")
4. For each constraint, ask:
   - What system property would BREAK if this constraint disappeared?
   - If the answer is "nothing meaningful" → assumed constraint
   - If the answer is a physical/logical requirement → genuine constraint
5. For assumed constraints, generate a relaxation variant
6. Combine genuine constraints with relaxation variants → reframed problem

## Example

**Input**: "We can't improve code quality because we don't have time for refactoring"

**Analysis**:
- Stated constraint: No time for refactoring
- Assumed constraints:
  - Quality requires dedicated refactoring time
  - Refactoring and feature work are separate activities
  - Quality work must be scheduled in advance

**Reframing**:
- Genuine: Features must ship (time is real)
- Relaxation: Quality can be improved during feature work (Boy Scout Rule)
- Freedom: Continuous quality improvement eliminates need for dedicated refactoring

## When to Use

- Problems that feel stuck ("we can't because...")
- Processes that haven't changed in years
- Assumptions that block creative solutions
- Pair with `divergence_lens` for maximum perspective generation

## Quality Check

Remove the constraint classification step. Does the output collapse to unexamined assumption acceptance? If yes, the lens is contributing.

## Complements

- `divergence_lens`: Generates perspectives; `constraint_lens` generates freedom
- `convergence_lens`: Finds shared ground; `constraint_lens` finds hidden walls
