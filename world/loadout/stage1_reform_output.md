# Stage 1: Reform Output

## Input Problem
"The skill economy lacks sufficient skill diversity and quality verification."

## Stage 1: Constraint Inversion

### Extracted Constraints
1. "Skills must exist in loadout" → What if skills DON'T exist? → Skill gap problem
2. "Skills must pass the gate" → What if we don't test before shipping? → Gate failures
3. "Skills must be unique" → What if all skills converge to same pattern? → Redundancy

### Inverted Solutions (Top 3)
1. **Gap-Fill Approach**: Create skills that fill identified loadout gaps
2. **Quality-First Approach**: Verify skills BEFORE crafting them
3. **Convergence-Avoidance Approach**: Ensure each skill has distinct value

## Stage 2: Second-Order Analysis

### Candidate 1: Gap-Fill
- Q1: Identify missing skill types → craft them → list them
- Q2: Benefits: more skills available; Risks: might create skills nobody needs
- Q3: If gap analysis is wrong → crafted skill fails the gate

### Candidate 2: Quality-First
- Q1: Write test → craft skill → verify → list
- Q2: Benefits: higher pass rate; Risks: slower iteration
- Q3: If test is wrong → good skills rejected

### Candidate 3: Convergence-Avoidance
- Q1: Check existing skills → craft differently → list
- Q2: Benefits: differentiation; Risks: niche skills nobody buys
- Q3: If differentiation fails → skill is just another duplicate

## Stage 3: Synthesis

Scoring: `constraint_depth × second_order_coverage`
- Gap-Fill: 3 × 2 = 6
- Quality-First: 2 × 3 = 6  
- Convergence-Avoidance: 2 × 2 = 4

**Final Reframe**: "Craft skills that address VERIFIED gaps in the loadout, ensuring each new skill passes a pre-flight verification BEFORE being listed."

## Confidence: HIGH

The reframe is substantively different because:
- Original: vague "lack of diversity"
- Reframed: specific "verified gaps + pre-flight verification"
