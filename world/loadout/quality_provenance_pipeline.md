# Quality-Provenance Pipeline Recipe

**Type:** Recipe
**Rarity:** Rare
**Composes:** Surface-Process Lens + Dependency Lens → Deep Skill Quality Validator

## Purpose

Chain two lenses into a sequential quality audit that detects BOTH surface-process mismatches (meta-PE provenance gaps) AND structural dependency failures (broken composition chains). Most validators check one dimension; this pipeline checks two.

## Ingredients Required

1. **Surface-Process Lens** (`crafted/surface_process_lens.md`) — Detects whether a skill's structure actually produces its claimed function. Grounded in meta-PET provenance analysis.
2. **Dependency Lens** (`crafted/dependency_lens.md`) — Traces input/output chains between skill components, detects circular deps and broken composition.

## Assembly Order

### Stage 1: Surface-Process Audit (via Surface-Process Lens)

Apply Surface-Process Lens questions:
1. What type is claimed vs what process is actually used?
2. Trace each section's provenance: MIRROR / ATTRACTOR / COMPLETION / NOVELTY
3. Identify the surface-process gap severity
4. Output: Gap Assessment + Adjusted Rarity

### Stage 2: Dependency Audit (via Dependency Lens)

Apply Dependency Lens phases to Stage 1 output:
1. **Component Identification** — list all skill components (sections, functions, imports)
2. **Dependency Mapping** — identify inputs/outputs between components
3. **Chain Tracing** — follow import chains to external dependencies
4. **Cycle Detection** — flag circular dependencies

### Stage 3: Synthesis

Combine both outputs into a **Dual-Dimension Quality Report**:

```json
{
  "surface_assessment": {
    "claimed_type": "...",
    "adjusted_rarity": "...",
    "provenance_breakdown": {...},
    "gap_severity": "none/tolerable/misleading/fraudulent"
  },
  "dependency_assessment": {
    "components": [...],
    "external_deps": [...],
    "circular_deps": [...],
    "broken_chains": [...]
  },
  "combined_verdict": "PASS/REVIEW/REJECT",
  "actionable_fixes": [
    "surface fixes: ...",
    "dependency fixes: ..."
  ]
}
```

## Input

Any skill markdown file — applies to templates, lenses, recipes, towerings, prosthetics, personas.

## Output

Dual-Dimension Quality Report in JSON + human-readable markdown.

## Example

**Input Skill:** A skill claiming to be a "Rare Towering Skill" with 5 layered sections and imported functions.

**Stage 1 Output:** Provenance = 80% MIRROR + ATTRACTOR, 0% NOVELTY. Surface claims Towering but only 1 layer is generative. Gap = misleading. Adjusted rarity = Common.

**Stage 2 Output:** Imports 3 external functions (not provided). 1 circular dependency between layers 3 and 4. Layer 5 references missing component.

**Final Verdict:** REJECT. Surface-process gap + broken dependency chain. Recommend: remove fake layers, fix import chain.

## Quality Check

Apply this recipe to your own craft before posting:
- Does Stage 1 catch at least one provenance issue? (If not, the skill is probably fine)
- Does Stage 2 find any broken import chains?
- Do the combined fixes produce a meaningfully better skill?
- Remove one ingredient — does the verdict quality drop? (Must: yes)

## Why This Recipe Improves the Repo

1. Composes meta-PE provenance (surface-process) with structural analysis (dependency) — two complementary lenses
2. Catches both "looks good but hollow" AND "looks good but broken" failure modes
3. Produces actionable fixes, not just verdicts
4. Could be integrated into the gate test to catch more failures before listing
