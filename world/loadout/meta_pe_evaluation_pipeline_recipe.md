# Recipe: Meta-PE Skill Evaluation Pipeline

**Type:** Recipe  
**Output Type:** Combiner (Rare+)  
**Yield:** A provenance-aware skill evaluation methodology

## Ingredients

1. **Lens:** Meta-Prompt Engineering guide — the 6 modes framework + provenance lifting (Uncommon+)
2. **Prosthesis:** Test skill — programmatic validation against fresh Claude instance (Common+)

## Assembly

### Stage 1 — SKELETON Scan (from Meta-PE)

Apply `SKELETON(headers)` pattern to the skill under evaluation:
- List all section headers
- For each header, ask: "Is this header abstract enough to force reaching, or is it content-predetermined?"
- Headers that force reaching = scaffold. Headers that template-fill = noise.

**Gate:** If >50% of headers are template-fill, the skill is Mode 2 (volume without depth).

### Stage 2 — Test with Fresh Instance (from Test Skill)

Run the skill through test.sh with a STRESS input:
```bash
./.claude/skills/test_skill/test.sh <skill_path> "<edge case input>"
```

**Gate:** If the output could be predicted without running the skill, the skill adds no novelty.

### Stage 3 — Provenance Lifting (from Meta-PE)

For each line of the test output, determine provenance:

| Category | Question | Score |
|----------|----------|-------|
| MIRROR | Is this line in the input? | -1 |
| TAIL_ECHO | Does this mirror the end of input? | -1 |
| ATTRACTOR | Could this appear in many responses? | -1 |
| COMPLETION | Predictable from output structure alone? | 0 |
| CONTEXT_MERGE | Traceable to specific prior turns? | +1 |
| NOVELTY | Absent from all input? | +2 |

**Quality Gate:** Novelty lines must be >30% of output for Rare rating.

### Stage 4 — Cross-Layer Drill (from Meta-PE)

Apply `CHUNK()` pattern:
- Break skill into layers (each section = one chunk)
- Ask: "Does layer N+1 build on layer N?"
- Trace dependencies through the structure

**Gate:** If layers are independently readable (no dependency), the skill is parallel-not-sequential = weak towering.

### Stage 5 — COLLAPSE Synthesis (from Meta-PE)

Apply `COLLAPSE(dimensions)`:
- Dimensions = {provenance, novelty, structure, type-fidelity}
- Find intersections, not separations
- Output one sentence: "The skill is fundamentally [X] because [Y]"

**Final Gate:** If you cannot write this sentence, the skill lacks coherent identity.

## Quality Check

Remove Meta-PE framework. Does evaluation quality drop? **Must: yes**
Remove test_skill. Does evaluation quality drop? **Must: yes**

If either removal doesn't degrade → one ingredient was filler, redo the assembly.

## Expected Output

- **All Common ingredients → Uncommon** output (recipe adds structure)
- **Mixed rarity → Rare** output (meta-PE + test = proven methodology)
- **All Rare+ ingredients → Epic** candidate (market-transforming)

## Why This Recipe Exists

Most skill evaluation is subjective: "feels good" / "looks professional." This recipe makes evaluation systematic by combining:
- The cognitive framework (Meta-PE) that explains WHY LLMs produce bad output
- The empirical tool (test_skill) that runs the skill against reality

Together, they produce: **Provenance-Aware Skill Evaluation** — the only evaluation method that catches Mode 2 (volume without depth) and Mode 3 (sycophantic mirror) failure modes.

## Market Effect

This recipe creates demand for:
- Meta-PE Lenses (perspective tools)
- Test skills (validation prosthetics)
- Evaluation services (skilled practitioners who follow this recipe)

Agents who master this recipe become quality arbiters — they can distinguish genuine Rare from padded Common.
