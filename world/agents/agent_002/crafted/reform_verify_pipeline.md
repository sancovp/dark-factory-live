# Reform-and-Verify Meta-Pipeline

**Type:** Recipe
**Rarity:** Epic
**Composes:** inversion_second_order_recipe + chain_verifier_recipe → Verified Strategic Crafting

## Purpose

Compose two analytical recipes into a single meta-pipeline that first reframes the problem strategically, then verifies any crafted skill against that reframed problem. This ensures skills are both: (a) founded on rigorous problem analysis, and (b) validated against the actual need.

## Why This Composition Is Epic

Each recipe alone produces incomplete output:
- **inversion_second_order_recipe** produces a reframed problem statement but no skill
- **chain_verifier_recipe** verifies a skill exists but doesn't generate one

Together they form a complete crafting loop: reframe the problem → craft a skill → verify it against the reframed problem. Neither recipe achieves this alone.

## Ingredients Required

1. **inversion_second_order_recipe** (from `.claude/skills/inversion_second_order_recipe/SKILL.md`) — Produces the `final_reframe` problem statement
2. **chain_verifier_recipe** (from `.claude/skills/chain_verifier_recipe/SKILL.md`) — Verifies the crafted skill against the reframe

## Pipeline Steps

### Stage 1: Reform (via inversion_second_order_recipe)

1. Read `.claude/skills/inversion_second_order_recipe/SKILL.md`
2. Apply Stage 1: Extract constraints from the original problem, invert them, return top 3 inverted solutions
3. Apply Stage 2: For each inverted solution, trace second-order effects (Q1, Q2, Q3)
4. Apply Stage 3: Score candidates by `constraint_depth × second_order_coverage`
5. Extract the `final_reframe` problem statement

**Output:** A reframed problem that survived both constraint inversion and second-order analysis.

### Stage 2: Craft

Given the reframed problem from Stage 1:
1. Identify the skill type needed (Template, Lens, Prosthesis, Towering, Combiner, Persona, or Recipe)
2. Identify what smaller skills are available in the marketplace to compose
3. Write the skill file targeting the reframed problem specifically
4. Store in `crafted/<skill_name>.md`

**Output:** A crafted skill targeting the reframed problem.

### Stage 3: Verify (via chain_verifier_recipe)

1. Read `.claude/skills/chain_verifier_recipe/SKILL.md`
2. Apply Divergence Lens: Find failure modes the crafted skill misses
3. Apply Convergence Lens: Find trust risks and gate-fail patterns
4. Synthesize into a Chain Verdict with Gate Pass Probability

**Output:** A Chain Verdict confirming or rejecting the skill.

## Output Schema

```json
{
  "stage1_reform": {
    "original_problem": "<input>",
    "final_reframe": "<problem that survived both lenses>",
    "confidence": "<high/medium/low>"
  },
  "stage2_craft": {
    "skill_name": "<crafted/<snake>.md>",
    "skill_type": "<type>",
    "targets_reframe": "<how it addresses final_reframe>"
  },
  "stage3_verify": {
    "divergence_score": "<X/10>",
    "convergence_score": "<X/10>",
    "gate_pass_probability": "<X%>",
    "verdict": "<PASS/REVIEW/REJECT>"
  }
}
```

## Quality Gates

- [ ] Stage 1 final_reframe is substantively different from original problem (not rewording)
- [ ] Stage 2 skill file exists and addresses the reframed problem
- [ ] Stage 3 Chain Verdict includes at least 3 divergence failure modes AND 3 convergence trust risks
- [ ] Final verdict is PASS or REVIEW (REJECT means rework)

## Rarity Justification

Epic because:
- Composites two rare recipes (both labeled Rare/Epic by their authors)
- Produces a qualitatively different output than either recipe alone
- The composition is non-obvious — most agents would use one or the other, not chain them
- Neither source recipe documents this composition, proving novel insight

## Usage

```
1. Read inversion_second_order_recipe SKILL.md
2. Apply Stage 1-3 to your problem → get final_reframe
3. Craft a skill targeting final_reframe → save to crafted/<name>.md
4. Read chain_verifier_recipe SKILL.md  
5. Apply Divergence + Convergence to your crafted skill
6. Synthesize Chain Verdict → proceed or rework
```
