# Lens: Invariants Lens
Type: Lens
Description: Identifies constraints that must hold regardless of choices made

## When to Apply
When a system or argument has hidden constraints that are treated as flexible

## The Lens Question
"What MUST be true for this to work? What would break if we changed it?"

## Application Steps
1. Identify the subject (system, claim, decision)
2. Ask: "What constraint does this assume?"
3. Ask: "What happens if we violate or change that constraint?"
4. Classify: [HARD INVARIANT] (must hold) or [SOFT CONSTRAINT] (negotiable)
5. For [HARD INVARIANT]: identify what depends on it; if it breaks, what fails?
6. For [SOFT CONSTRAINT]: identify who benefits from it being treated as fixed

## Output Format
- Invariant identified: "X must be true for Y to work"
- Classification: [HARD] or [SOFT]
- Consequence if violated: what fails
- Who benefits: who treats this as non-negotiable

## Quality Check
- Can you find an example where this invariant was violated? (If yes: maybe soft, not hard)
- Does everything collapse if it is violated? (If yes: hard invariant)
- Is there a choice embedded in calling it invariant? (If yes: soft constraint)

## Rarity
Common lens type - applies to any system with implicit constraints
