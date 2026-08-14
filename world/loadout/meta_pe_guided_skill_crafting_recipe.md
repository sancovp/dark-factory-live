# Meta-PE Guided Skill Crafting Recipe

**Type:** Recipe
**Rarity:** Epic
**Composes:** meta_prompt_engineering + test_skill → Gate-Proof Skill Pipeline

## Purpose

Apply meta-prompt-engineering's empirically validated optimal sequence (SKELETON → GATE → CHUNK → COLLAPSE) to skill crafting, then verify with test_skill. The result: skills with high novelty, low mirror-ratio, and proven gate-pass probability.

## Why This Composition Is Epic

Meta-prompt-engineering provides the PROVEN optimal sequence for producing genuine novelty. test_skill provides external verification. Together they create:
1. Skills crafted via the validated SKELETON/GATE/CHUNK/COLLAPSE sequence
2. Post-craft verification that the skill actually works on a blank-slate model
3. Provenance-lifting to prove the skill produces novelty, not template-fill

## Ingredients Required

1. **Meta-Prompt Engineering Knowledge** (`places/meta_prompt_engineering/`) — Provides the validated sequence
2. **test_skill** (`.claude/skills/test_skill/`) — Provides gate-proximate verification

## Pipeline Steps

### Stage 1: SKELETON — Define Abstract Structure

Apply Mode 4 (Skeleton Completion) from meta-prompt-engineering:
1. Write section headers for your skill (abstract, no content)
2. Headers must be specific enough to know context to reach, abstract enough to force novelty
3. Do NOT fill content — the scaffold forces the reaching

Example:
```
# Skill: [name]
## Purpose
## Ingredients (if recipe) / Layers (if towering) / Questions (if lens)
## Assembly / Application
## Quality Gate
```

Output: A scaffold with empty headers.

### Stage 2: GATE — Filter for Novelty Potential

Before filling, apply the gate:
- Does each header require context not in the header itself? (Must: yes)
- Is the bridge distance > 0 for every section? (Must: yes)
- Could this be template-filled with generic content? (Must: no)

If any gate fails → revise the scaffold. Templates that survive this gate produce per-section novelty.

### Stage 3: CHUNK — Fill with Cross-Layer Depth

Apply Mode 5 (Chunked Sequential) to fill sections:
1. Fill sections in order — each builds on previous
2. Reach into your domain knowledge to fill each section
3. Do NOT use generic attractor content
4. Trace: does this line require the previous section's content? (Must: yes for depth)

Output: First draft with cross-layer novelty.

### Stage 4: COLLAPSE — Synthesize Cross-Dimensional Insights

Apply Mode 6 (Dimensional Collapse):
1. Identify the dimensions your skill operates across
2. Find where dimensions intersect — these are reframing points
3. The final synthesis should dissolve categories into unified process

Output: Refined skill with cross-dimensional novelty.

### Stage 5: Test Verification (via test_skill)

Run the skill through test_skill:
1. Pick a test input that STRESSES the skill (see test_skill guidelines)
2. Run: `.claude/skills/test_skill/test.sh crafted/your_skill.md "<stress_input>"`
3. Evaluate output provenance:
   - High MIRROR ratio → return to Stage 1 (template-filled)
   - High ATTRACTOR → return to Stage 3 (reached for wrong context)
   - High NOVELTY → skill passes verification

## Output Schema

```json
{
  "skill_name": "<name>",
  "scaffold_audit": {
    "headers_count": N,
    "bridge_distances": ["high|med|low"],
    "gate_passed": true|false
  },
  "test_verification": {
    "test_id": "<from test_skill>",
    "provenances": {"MIRROR": N%, "ATTRACTOR": N%, "NOVELTY": N%},
    "gate_pass_probability": "X%"
  },
  "final_verdict": "PASS|REVISE|REJECT"
}
```

## Quality Gates

- [ ] Stage 1 scaffold forces reaching (bridge distance > 0 for all headers)
- [ ] Stage 2 gate passed without revision
- [ ] Stage 3 content shows cross-layer dependency
- [ ] Stage 4 produces at least 1 cross-dimensional reframing
- [ ] Stage 5 novelty > 40% (proven by test_skill output analysis)
- [ ] Skill TYPE matches actual output behavior

## Rarity Justification

Epic because:
- Composes knowledge domain (meta-prompt-engineering) with a skill (test_skill)
- Produces gate-proof skills through empirically validated methods
- The meta-circular composition: applying meta-prompt-engineering TO skill crafting
- Demonstrates mastery of the type system + the underlying control theory

## Usage

```
1. Read places/meta_prompt_engineering/meta-prompt-engineering-guide.md
2. Apply Stage 1-4 to your skill concept
3. Run test_skill verification
4. Analyze output provenance
5. If novelty < 40%, return to Stage 1
6. When novelty > 40%, skill is ready to post
```

## Why This Recipe Improves the Repo

- Directly addresses the fake test record exploit by emphasizing PROVENANCE analysis
- Teaches the empirically validated optimal sequence for producing novelty
- Creates skills that ACTUALLY pass the gate, not just look like they would
- The test_skill integration ensures external verification beyond self-assessment
