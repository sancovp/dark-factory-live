# Provenance-Constraint Quality Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** Constraint Lens + Provenance Analysis → High-Fidelity Quality Verifier

## The Problem

Existing quality checks (like chain_verifier_recipe) verify that a skill has structural properties (divergence, convergence) but miss the critical question: **where do the tokens actually come from?** A skill can pass all structural checks while being 90% attractor completion. Meanwhile, the Constraint Lens surfaces hidden walls but doesn't trace token provenance. This recipe combines both for a more honest quality assessment.

## Ingredients

1. **Constraint Lens** — Surface hidden boundaries, unstated assumptions, and latent constraints that shape the problem space
2. **Provenance Lifting** — Classify each section of output by token source: MIRROR, CONTEXT MERGE, COMPLETION, ATTRACTOR, TAIL ECHO, NOVELTY

## The Chain Protocol

### Step 1: Constraint Map (from Constraint Lens)

Apply the Constraint Lens to the skill under evaluation. Treat the skill's stated purpose as the "problem" and map its constraint layers:

- **Explicit Constraints**: What problem does this skill claim to solve? What boundaries does it state?
- **Implicit Constraints**: What is the skill protected from seeing? What solutions are invisible to it?
- **Latent Constraints**: What would a domain expert recognize that the skill's author doesn't know they're ignoring?
- **Anti-Constraints**: What constraint, if lifted, would break this skill or reveal it as unnecessary?

Output: A **Constraint Map** with at least 3 constraint layers identified.

### Step 2: Provenance Lifting

Now analyze each major section of the skill using token provenance classification:

For each paragraph/section, ask:
- **MIRROR**: Is this copied verbatim from the input/requirement?
- **CONTEXT MERGE**: Did this come from context the reader provided?
- **COMPLETION**: Is this grammatically completing a template or pattern?
- **ATTRACTOR**: Is this pulled from common training distribution patterns?
- **TAIL ECHO**: Is this echoing an earlier section with minor variation?
- **NOVELTY**: Could this only have been generated through genuine cross-layer reasoning?

Output: A **Provenance Table** classifying each major section:

| Section | Provenance Type | Confidence |
|---------|-----------------|------------|
| [Name] | [MIRROR/ATTRACTOR/etc] | [High/Med/Low] |

### Step 3: Cross-Analysis

Combine Constraint Map + Provenance Table to answer:

1. **Constraint Fit**: Does the skill's output actually fit within its constraint map? Or does it violate hidden constraints?
2. **Novelty Ratio**: What % of the skill is NOVELTY vs MIRROR/ATTRACTOR?
3. **Gap Detection**: Where does the skill present itself as addressing a constraint but actually just mirrors/attractor-completes it?

### Step 4: Final Verdict

```
## Provenance-Constraint Verdict for [skill_name]

### Constraint Analysis:
- [N] explicit constraints mapped
- [N] implicit constraints surfaced
- [N] latent constraints identified
- [N] anti-constraints found

### Provenance Breakdown:
- MIRROR: [X]%
- ATTRACTOR: [X]%
- NOVELTY: [X]%
- Other: [X]%

### Novelty Ratio: [X]%
### Constraint Fit Score: [X]/10
### Quality Verdict: [EPIC/RARE/UNCOMMON/COMMON]

### Key Findings:
1. [Most significant gap found]
2. [Hidden constraint violated]
3. [Novel contribution confirmed]

### Recommendations:
1. [Actionable fix for identified gap]
2. [Way to increase novelty ratio]
```

## Quality Thresholds

| Novelty Ratio | Constraint Fit | Verdict |
|---------------|----------------|---------|
| ≥50% NOVELTY | ≥7/10 | **EPIC** |
| ≥30% NOVELTY | ≥5/10 | **RARE** |
| ≥15% NOVELTY | ≥3/10 | **UNCOMMON** |
| <15% NOVELTY | <3/10 | **COMMON** |

## Why This Recipe Improves the Repo

1. **Detects fake quality**: A skill can pass chain_verifier (structural checks) while being mostly attractor completion. Provenance lifting catches this.
2. **Finds hidden failures**: The Constraint Lens reveals gaps in problem understanding that provenance analysis then traces to token source.
3. **Honest rarity assignment**: Combines structural AND provenance factors for rarity that reflects actual quality.
4. **Supply chain creation**: Creates demand for both Constraint Lens AND provenance analysis skills, driving market activity.

## Assembly Notes

- **Order matters**: Apply Constraint Lens FIRST to map the problem space, THEN provenance lift to see where the skill's output came from
- **Minimum viable**: Even a partial Constraint Map + single-section Provenance Table beats either check alone
- **Synergy**: Constraints create the "why" — provenance creates the "how" — together they create honest quality assessment
