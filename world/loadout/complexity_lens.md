# Complexity Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Reframes:** Problems through computational complexity and scaling behavior

## The Problem

Most analytical lenses focus on correctness, convergence, or dependencies. None systematically ask: how does this SCALE? A solution that works for 3 cases might fail for 300. The Complexity Lens forces this scaling question before any skill is trusted.

## The Lens Questions

Apply these questions to any problem or skill BEFORE accepting it:

### 1. Input Size Sensitivity
- What happens when input grows 10x? 100x?
- Does the solution remain tractable (polynomial) or explode (exponential)?
- Is there an implicit assumption that input is "small enough"?

### 2. Composition Complexity
- When skills compose, does complexity multiply or stay bounded?
- For each new skill added to a pipeline, how does total complexity change?
- Can the pipeline handle N skills, or does it assume K ≤ 3?

### 3. State Explosion
- Does the skill accumulate state over time?
- Does memory/processing grow with history length?
- For iterative calls: is there a bound or does it grow unbounded?

### 4. Edge Case Density
- What percentage of inputs are "easy"?
- What happens in the worst case vs average case?
- Are edge cases rare enough to ignore, or common enough to matter?

## When to Apply

Apply this lens:
- BEFORE accepting any skill as production-ready
- DURING pipeline design to catch scaling risks
- AFTER any "works on my example" confidence to check generalizability

## Output Format

For any skill under evaluation:

## Complexity Assessment: [skill_name]

### Scaling Risk: [LOW|MEDIUM|HIGH|UNKNOWN]
- Input size sensitivity: [description]
- Composition behavior: [description]
- State growth: [description]

### Edge Case Exposure: [X% of inputs problematic]
- Worst case: [description]
- Typical case: [description]

### Scaling Recommendation:
- [If HIGH/UNKNOWN: suggest refactoring or bounds]
- [If LOW: confirm with specific large-scale test]

### Verdict: [ACCEPT|WARNING|REJECT]

## Quality Gates

A lens application is VALID only if:
- At least 2 scaling questions answered with evidence
- Edge case density is quantified (even roughly)
- Verdict matches the analysis (no "LOW risk" + "REJECT" without justification)

## Rarity Rationale

Uncommon — computational complexity analysis is a well-established discipline, but applying it to skill/economy analysis is novel. The lens doesn't DO complexity math; it ASKS the complexity questions at decision time.
