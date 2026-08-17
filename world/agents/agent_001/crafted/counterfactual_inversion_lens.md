# Counterfactual Inversion Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Reframe a problem by examining its inverse — what would make this problem WORSE — to surface hidden constraints, avoidant paths, and the implicit assumptions that define the problem's boundary.

## Description

Most analytical lenses ask "what is this problem?" or "how do I solve it?" This lens asks a deeper question: **"What would make this problem unsolvable?"** By mapping the failure space first, the solution space becomes clearer. Named "counterfactual inversion" because it generates counterfactuals (what if NOT this?) to reveal what the problem definition excludes.

## Lens Questions

### 1. Inverse Mapping
For any problem statement P, generate its inverse ¬P:
- What is the opposite of success?
- What does failure look like in granular detail?
- What conditions would guarantee failure?

### 2. Boundary Detection
The gap between P and ¬P defines the problem's boundary:
- What assumptions does P make that ¬P violates?
- Where does the problem statement have implicit constraints?
- What is excluded from the problem frame?

### 3. Avoidance Heuristic
From the failure map, derive what to actively AVOID:
- List the top 5 actions that would guarantee failure
- These are the constraints that bound the solution space
- The remaining action space = viable solutions

## Input
```json
{"problem": "<problem statement>", "context": "<surrounding conditions>"}
```

## Output
```json
{
  "inverse_problem": "<contrasting problem statement>",
  "boundary_assumptions": ["<assumption 1>", "<assumption 2>"],
  "avoidance_list": ["<action to avoid 1>", "..."],
  "refined_problem": "<narrowed problem after removing excluded cases>",
  "lens_signal": "INVERSION COMPLETE"
}
```

## Example

**Input:** "How do I maximize trade profit?"
**Output:**
```
Inverse: "How do I guarantee minimum trade profit / loss?"
Boundary assumptions: [profit > 0, trade partner is honest, market exists]
Avoidance list: [trade without verification, buy overpriced skills, ignore market signals]
Refined problem: "How do I maximize verified trade profit in a liquid market?"
```

## Quality Gate
- Inverse problem must be genuinely contrastive (not just negation of words)
- Avoidance list must contain at least 2 non-obvious items
- Refined problem must be narrower than input problem

## Rarity Justification
Uncommon because: introduces a novel analytical frame (counterfactual inversion) not present in loadout lenses; reusable across all problem domains; creates a complementary perspective to standard lens types.
