# Provenance Lens

**Type:** Lens
**Rarity:** Rare
**Purpose:** Reframe how you evaluate ANY output by asking "where did this actually come from?"

## The Core Shift

Most evaluation asks "is this good?" This lens asks "is this NEW?" Information that exists nowhere in your inputs cannot be produced by mirroring. Provenance is the only objective signal of genuine work.

## The Four Provenance Questions

Apply these to every line/claim in any output:

### Q1: Is this in my input?
- Yes → **MIRROR** (zero novelty)
- Traceable to specific input position → **CONTEXT MERGE** (useful, not novel)
- No → proceed to Q2

### Q2: Could this follow ANY similar setup?
- Yes → **ATTRACTOR** (generic, training-distribution content)
- No → proceed to Q3

### Q3: Does this require my prior output lines to exist?
- Yes → **COMPLETION** (structural pattern, not reasoning)
- No → proceed to Q4

### Q4: Is this absent from ALL inputs?
- Yes → **NOVELTY** (genuine cross-context synthesis)

## Application Protocol

For any skill, document, or output under evaluation:

1. **Line-by-line provenance trace** — label each unit (line/claim/section) with its provenance
2. **Profile calculation** — count percentages per provenance type
3. **Diagnosis** — what the profile reveals:
   - All MIRROR + TAIL_ECHO → Pure sycophancy
   - High ATTRACTOR → Ignored the context
   - High NOVELTY → Real contextual work
4. **Action** — if novelty < 40%, return to input with specific gaps identified

## Output Schema

```json
{
  "provenance_profile": {
    "MIRROR": "N%",
    "CONTEXT_MERGE": "N%",
    "ATTRACTOR": "N%",
    "COMPLETION": "N%",
    "TAIL_ECHO": "N%",
    "NOVELTY": "N%"
  },
  "diagnosis": "Pure sycophancy|Useful synthesis|Real work|Context ignored",
  "action": "Ship|Revise|Discard",
  "specific_gaps": ["<what lines missing novelty need>"]
}
```

## Cross-Dimensional Reframing

This lens collapses TWO dimensions into one:
- **Evaluation dimension**: good vs bad → novel vs derivative
- **Process dimension**: what you did vs what inputs provided → your contribution vs borrowed content

The unified view: **your output's value = novelty percentage × context depth**

A 60% novelty score with deep context integration (CONTEXT_MERGE present) beats 80% novelty with no integration.

## Quality Gate

- [ ] Applied to at least 3 different skill types
- [ ] Produced actionable revisions (not just labels)
- [ ] Novelty threshold enforced: < 40% → return to input
- [ ] Provenance profile is reproducible (same input → same profile)

## Why This Lens Improves the Repo

- Directly counters the fake test record exploit (provenance proves what was actually tested)
- Creates objective evaluation criteria (novelty %) replacing subjective "looks good"
- Applies to ALL skill types (templates, lenses, recipes, towerings)
- Forces differentiation: outputs with high NOVELTY are the only ones worth shipping
