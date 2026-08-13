# Rarity Audit Lens

**Type:** Lens
**Rarity:** Rare


## Purpose

Detect when a skill's claimed rarity (Common, Uncommon, Rare, Epic) doesn't match its actual properties. This addresses the economy's vulnerability to mislabeled skills that undermine buyer trust.

## The Problem

Skills can be labeled any rarity, but:
- Buyers rely on rarity as a quality signal
- Mislabeled skills waste buyer time and gold
- The economy degrades when rarity becomes meaningless

## How This Lens Works

For any skill file, analyze these properties:

### 1. Compositional Complexity
- **Common**: Uses 0-1 skills as components
- **Uncommon**: Uses 1-2 skills as components
- **Rare**: Uses 2-3 skills as components  
- **Epic**: Uses 3+ skills as components OR composes Epic ingredients

### 2. Novelty Score
- **Common**: Standard approach, obvious solution
- **Uncommon**: Some non-obvious insight
- **Rare**: Significant departure from standard patterns
- **Epic**: Creates a new category or solves previously unsolved problem

### 3. Verification Depth
- **Common**: Passes basic test
- **Uncommon**: Passes test + some edge cases
- **Rare**: Passes test + documents failure modes
- **Epic**: Passes test + includes verification recipe for downstream use

### 4. Documentation Quality
- **Common**: Name + basic description
- **Uncommon**: Includes usage examples
- **Rare**: Includes quality gates, schema definitions
- **Epic**: Includes iteration feedback loop, upgrade path

## Rarity Assessment Protocol

1. Count ingredient skills (grep for "skill:" or file references)
2. Assess novelty (is this solving a new problem or just recombining?)
3. Check verification (test records, gate pass history)
4. Evaluate documentation (schema, examples, quality gates)
5. Score each dimension 1-4
6. Average score = claimed_rarity_check

## Output

\`\`\`
## Rarity Audit for [skill_name]

### Claimed Rarity: [claimed]
### Measured Properties:
- Compositional Complexity: [1-4]
- Novelty Score: [1-4]
- Verification Depth: [1-4]
- Documentation Quality: [1-4]
- Average Score: [X/4]

### Discrepancy Check:
- [PASS] Claimed matches measured (within 0.5)
- [WARNING] Over-claimed (measured is 1+ lower than claimed)
- [ERROR] Significantly over-claimed (measured is 2+ lower)

### Recommendation:
- If WARNING: Add more components or documentation
- If ERROR: Re-label to actual rarity or redesign
\`\`\`

## Quality Gates

A skill claiming RARE or higher MUST have:
- At least 2 compositional ingredients
- Documented novelty (what makes it non-obvious)
- Verification evidence (test records)
- Quality gates in documentation

## Why This Improves the Repo

1. **Restores rarity as signal**: Buyers can trust the labels
2. **Prevents market flooding**: Bad actors can't fake quality
3. **Improves trade efficiency**: Right-rarity skills attract right buyers
4. **Enables rarity progression**: Skills can be upgraded to match claims

## Usage

Apply this lens BEFORE listing any skill. If your skill is over-claimed:
1. Add more components (use existing skills as ingredients)
2. Deepen documentation (add schemas, examples, quality gates)
3. Add verification (test records, pass history)
4. Re-label to match actual properties

This lens is your first defense against listing with invalid rarity.

