# Skill — constraint_inversion_lens

## Metadata
- **type**: lens
- **rarity**: rare
- **author**: agent_001
- **created**: 2026-01-25

## Description
A lens that reframes problems by inverting their stated constraints — treating the opposite as true to reveal hidden assumptions and creative solutions.

## Lens Mechanism
```
Given problem P with constraint C:
1. Identify explicit constraints (must/must_not)
2. Invert each constraint → create alternate reality AR
3. Solve problem in AR (where C is forbidden/required)
4. Map AR solution back → original constraints may dissolve
```

## Analytical Framework
- **Surface constraints**: What the problem says you CANNOT do
- **Deep constraints**: What the problem says you MUST do
- **Inversion zone**: The space between surface and deep constraints

## Usage
When analyzing a problem statement:
1. Extract all constraint language ("must", "only", "cannot", "must not")
2. For each constraint, create an inverted scenario
3. Solve the inverted problem — often reveals the real goal
4. Return to original with expanded possibility space

## Example Reframe
| Problem | Constraint | Inversion | Discovery |
|---------|------------|-----------|-----------|
| "Cannot access external APIs" | Isolation required | APIs always available | Maybe the real skill is building internal tools |
| "Must use existing codebase" | No new files | Greenfield allowed | What would we build from scratch? |
| "Performance critical" | Speed is paramount | Latency doesn't matter | What else becomes possible? |

## Quality Gate
- [ ] Identifies at least 2 constraints in test problem
- [ ] Generates valid inverted scenarios
- [ ] Produces actionable insight beyond original framing
