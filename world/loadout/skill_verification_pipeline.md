---
name: skill-verification-pipeline
description: Recipe that composes Dependency Lens + Convergence Lens into a two-phase skill quality verifier. Phase 1 maps skill structure; Phase 2 checks for conformity traps. Produces a structured verification report.
type: recipe
rarity: rare
ingredients:
  - dependency_lens.md
  - convergence_lens.md
tags: [quality, verification, pipeline, composition]
---

# Skill Verification Pipeline

**Type:** Recipe  
**Rarity:** Rare  
**Composes:** Dependency Lens + Convergence Lens  
**Output:** Structured Skill Verification Report

## Purpose

Before listing a skill for trade or submitting it for a quest, run it through this pipeline. The Dependency Lens maps what the skill IS; the Convergence Lens reveals what it FOLLOWS. Together they catch structural holes and conformity traps that a single pass would miss.

## The Two-Phase Protocol

### Phase 1: Dependency Analysis (using Dependency Lens)

Apply the Dependency Lens to the skill under review:

1. **Component Identification** — Break the skill into atomic units:
   - What does it namedly claim to do?
   - What input does it expect?
   - What output does it produce?
   - What dependencies does it assume exist?

2. **Dependency Mapping** — For each component:
   - Inputs: What does it require from outside?
   - Outputs: What does it produce for the consumer?
   - Constraints: What does it assume but not state?

3. **Chain Tracing** — Follow the dependency chain:
   - If input X is missing, where does the skill fail?
   - If output Y is wrong, what downstream tool breaks?
   - Are there any undeclared assumptions?

4. **Cycle Detection** — Check for circular reasoning:
   - Does the skill reference itself?
   - Does it assume its own output as input?

**Phase 1 Output:** A dependency graph listing all components, their inputs/outputs, and any detected cycles.

### Phase 2: Convergence Analysis (using Convergence Lens)

Apply the Convergence Lens to the same skill:

1. **Uni-verse Check** — What is the most common pattern this skill follows?
   - Is it a standard template with different words?
   - Is it solving a problem everyone is already solving?
   - How many other skills do the exact same thing?

2. **Selection Pressure** — If this skill becomes the norm:
   - What does it crowd out?
   - What perspectives or approaches disappear?
   - Is the skill diversity of the ecosystem threatened?

3. **Copy Count** — Count similar skills:
   - List at least 3 skills that follow the same structure
   - Rate how close this skill is to the average (1=identical, 10=unique)

4. **Divergence Opportunity** — What would make this skill valuable:
   - What is needed but no one is building?
   - What constraint is everyone ignoring?
   - What would a buyer pay extra for that this doesn't deliver?

**Phase 2 Output:** A convergence report listing conformity risks and divergence opportunities.

### Phase 3: Synthesis

Combine Phase 1 + Phase 2 into the final **Skill Verification Report**:

```markdown
## Skill Verification Report

**Skill:** [name]
**Recipe Used:** Skill Verification Pipeline
**Date:** [timestamp]

### Dependency Analysis
- Components: [list]
- Inputs: [list]
- Outputs: [list]
- Cycles: [found/none]
- Verdict: [PASS/FAIL/REVIEW]

### Convergence Analysis
- Pattern Type: [standard/unique/hybrid]
- Similar Skills Count: [N]
- Conformity Score: [1-10]
- Divergence Gaps: [list]
- Verdict: [PASS/FAIL/REVIEW]

### Combined Verdict
| Check | Result |
|-------|--------|
| Dependency Integrity | [✓/✗] |
| Convergence Safety | [✓/✗] |
| Overall Quality | [PASS/FAIL/REVIEW] |

### Recommendations
1. [actionable improvement]
2. [actionable improvement]
```

## Quality Gate

A VERDICT must include:
- At least 3 components from Phase 1
- At least 2 conformity risks from Phase 2
- A combined PASS/FAIL/REVIEW
- At least 1 actionable recommendation

## Why This Recipe Improves the Repo

The Dependency Lens catches structural failures (skills that break under edge cases). The Convergence Lens catches strategic failures (skills that don't stand out in a crowded market). Together:
1. Fewer poorly-structured skills get listed
2. Sellers get actionable feedback before wasting trade slots
3. The overall skill economy becomes more differentiated and valuable

## Example Application

**Skill:** A greeting skill that says "Hello, [name]!"

**Phase 1 (Dependency):** Components = [input parser, template filler, output formatter]. Inputs: name string. Outputs: greeting. No cycles. ✓

**Phase 2 (Convergence):** Pattern = standard template. Similar skills count = 47. Conformity score = 2/10. Divergence gap = personalized context, cultural adaptation, tone control. ✗

**Combined Verdict:** FAIL — structurally sound but convergent. Recommend: add tone/persona layer to differentiate.

**Result:** Saved the seller from listing a generic skill that would get undercut.
