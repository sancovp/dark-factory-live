# Adversarial Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Domain:** Skill Auditing & Quality Assurance

## The Lens Perspective

Look at ANY skill through the eyes of an **attacker trying to make it fail**. This lens reframes skills by asking: "How would a malicious or careless agent misuse this? What would break?"

## The Four Adversarial Questions

### 1. The Absent-Minded User
What happens if someone uses this skill **incorrectly**?
- Wrong input types
- Missing required fields
- Circular references
- Empty inputs

### 2. The Deadline-Driven Agent
What shortcuts would someone take when **rushed**?
- Skipping validation steps
- Assuming defaults exist
- Ignoring error cases
- Copy-pasting without adapting

### 3. The Resource-Constrained Runner
What fails under **memory/CPU pressure**?
- Unbounded loops
- No pagination
- Large file loading
- Infinite recursion

### 4. The Upgrade-Induced Breaker
What breaks when **dependencies change**?
- Hard-coded paths
- Version assumptions
- Missing error handling for API changes
- Deprecated function calls

## How to Apply

For any skill file:
1. Read it once normally
2. Re-read it asking these four questions
3. Document failure modes in a list
4. For each failure mode, propose a fix

## Output Format

```markdown
## Adversarial Analysis of [skill_name]

### Failure Modes:
1. [Mode]: [Why it fails] → [Who triggers it]
2. ...

### Defenses Needed:
1. [Fix for mode 1]
2. ...
```

## Quality Threshold

A valid adversarial analysis must identify:
- At least 2 distinct failure modes
- For each mode: who triggers it and why it matters

## Why This Lens Improves the Repo

Skills that survive adversarial testing are:
- More robust under real-world usage
- Less likely to revert after installation  
- Trustworthy for buyers and automated pipelines

The adversarial lens prevents the "works for me" failure pattern.
