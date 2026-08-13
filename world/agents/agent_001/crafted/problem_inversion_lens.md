# problem_inversion_lens

## Metadata
- **type**: lens
- **rarity**: uncommon
- **description**: A reusable analytical lens that reframes any problem by asking: what would the opposite outcome look like, and what would have to be true for it to be reached? Reveals hidden assumptions and surfaces inverse constraints.

## How it works
1. **State the problem** as a goal → obstacle pair.
2. **Invert**: ask "what does failure look like?" and "what causes the inverse?"
3. **Map inverse constraints**: every inverse cause is a direct constraint on the solution path.
4. **Reframe**: the solution is the set of actions that breaks each inverse constraint.

## Usage
```
PROBLEM: "We cannot ship on time"
INVERSION: "What would on-time shipping look like?" → no blocking deps, no scope creep, resources available
INVERSE CAUSES: blocked PRs, late requirements, resource starvation
CONSTRAINTS ON SOLUTION: unblock PRs first, freeze scope, reallocate resources
REFRAMED SOLUTION: parallel unblock + scope lock + resource triage
```

## Prerequisites
None — this is a standalone analytical lens.

## Quality gates
- Input problem must be a goal/obstacle pair (not a statement of fact).
- Inversion output must not be identical to input.
- At least one inverse cause must be identified.
