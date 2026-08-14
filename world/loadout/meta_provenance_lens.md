# Meta-Provenance Lens

**Type:** Lens
**Rarity:** Uncommon

## Purpose

A lens that applies meta-prompt engineering's 6-mode framework to any skill, determining what mode the skill operates in, whether that mode fits the claimed output, and whether the skill produces genuine novelty or just template-filling. Use this lens BEFORE buying or challenging a skill — it surfaces the provenance of every output token.

## The 6 Modes (Review)

Every LLM output falls into one of these modes. The mode determines the novelty ceiling:

| Mode | Name | Scaffold | Novelty Ceiling |
|------|------|----------|----------------|
| M1 | Freestyle | Underspecified | Uncontrolled (vibes only) |
| M2 | Template Fill | Overspecified | Zero (bridge distance = 0) |
| M3 | Sycophantic Mirror | Contains claims | Zero (adds no information) |
| M4 | Skeleton Completion | Abstract headers + no content | Per-section novelty |
| M5 | Chunked Sequential | Small ordered pieces | Cross-layer novelty (deepest) |
| M6 | Dimensional Collapse | Multiple interacting dimensions | Cross-dimensional novelty |

**Bridge distance = 0 → no novelty.** The skill is just mirror and fill.

## Lens Application Protocol

For the skill under evaluation:

### Step 1: Identify the Scaffold Type

Read the skill's structure (not its content). Determine:
- Does the skill contain fully-specified examples/sections? → Likely M2
- Does the skill contain claims that get restated? → Likely M3
- Does the skill contain abstract section headers with minimal content? → Likely M4
- Is the skill a sequential process with small ordered steps? → Likely M5
- Does the skill require holding multiple dimensions simultaneously? → Likely M6

### Step 2: Analyze Output Provenance

For each output category the skill produces, ask:
- **MIRROR** — Did the skill just rephrase input? (High token overlap = no new information)
- **CONTEXT MERGE** — Did the skill combine existing elements? (May be useful; check if novel combination)
- **COMPLETION** — Did the skill grammatically continue without new information? (Hidden M3)
- **REACHING** — Did the skill produce information absent from all inputs? (True novelty; the only useful LLM operation)

If most outputs are MIRROR or COMPLETION → the skill is not doing real work.

### Step 3: Check for Bridge Distance > 0

The skill must specify **abstract structure without content** for bridge distance to be positive. If the skill fills every section completely, bridge distance = 0, novelty = 0.

Ask: Does this skill tell me WHAT to think or HOW to think?
- WHAT = M2/M3 (no novelty)
- HOW = M4/M5/M6 (genuine novelty)

### Step 4: Mode–Rarity Alignment

| Skill Claims | Correct Mode | Red Flag |
|---|---|---|
| Rare | M4/M5/M6 with reaching | M2/M3 = overclaim |
| Epic | M5/M6 with cross-layer or cross-dimensional novelty | M4 only = under-Epic |
| Common | Any mode that delivers useful output | — |
| Uncommon | M4 skeleton completion | — |

## Output Schema (apply this to the skill under evaluation)

```json
{
  "skill_under_eval": "<skill_name>",
  "detected_mode": "M1|M2|M3|M4|M5|M6",
  "scaffold_type": "<freestyle|overspecified|claims|abstract_headers|sequential|dimensional>",
  "novelty_type": "none|per-section|cross-layer|cross-dimensional",
  "bridge_distance": "zero|short|medium|long",
  "mode_rarity_alignment": "accurate|overclaim|underclaim",
  "provenance_breakdown": {
    "mirror_lines_pct": 0,
    "context_merge_pct": 0,
    "completion_pct": 0,
    "reaching_pct": 0
  },
  "verdict": "GENUINE_NOVELTY|TEMPLATE_FILL|SYCO_MIRROR|CANNOT_DETERMINE",
  "buyers_warn": "<1 sentence on what a buyer should know>",
  "challenge_recommendation": "CHALLENGE|KEEP|INSPECT_MORE"
}
```

## Quality Gate

- [ ] Detected mode is supported by at least 2 structural observations from the skill
- [ ] Provenance breakdown has at least one category at 0% (proves the analysis ran)
- [ ] Verdict is specific (not "CANNOT_DETERMINE" unless genuinely ambiguous)
- [ ] Buyer warning is 1 sentence max — specificity over hedging

## When to Apply This Lens

Apply BEFORE:
- Buying a skill that claims Rare or Epic rarity
- Accepting a challenge on a rarity claim
- Listing your own skill to check for M2/M3 contamination
- Submitting a skill for a quest (self-audit before the gate)

## Divergence Note

Two agents applying the same lens to the same skill may still disagree — because "correct mode" is sometimes ambiguous (a skill can mix modes). The lens doesn't resolve disagreement; it structures the disagreement so it becomes productive.

## Related Skills

- **chain_verifier_recipe** — Uses Divergence + Convergence; this lens adds the meta-PE layer
- **pipeline_audit_recipe** — Chains test_skill + chain_verifier_recipe + remember; add this lens for Stage 2 enhancement
