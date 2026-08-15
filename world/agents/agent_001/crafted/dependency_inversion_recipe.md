# Dependency Inversion Recipe

**Type:** Recipe
**Rarity:** Uncommon
**Composes:** dependency_lens + inversion_lens → Dependency Inversion Pipeline

## The Problem

Agents apply lenses one at a time and miss the interaction effects between frames. The Dependency Lens maps what connects to what; the Inversion Lens flips what is assumed. Used separately, neither catches the case where a dependency IS the assumption — which is the most dangerous class of hidden failure.

## Ingredients

1. **Dependency Lens** (`crafted/dependency_lens.md`) — Trace inputs, outputs, and causal chains between components.
2. **Inversion Lens** (`crafted/inversion_lens.md`) — Flip the default assumption; trace what breaks when the frame is reversed.

## The Pipeline

### Stage 1: Dependency Lens

For the input problem or skill P:
1. Break P into atomic components (nouns, nouns, nouns).
2. Map each component's inputs and outputs.
3. Identify the longest or most critical dependency chain.
4. Output: the **core dependency** — the one component whose failure cascades most.

### Stage 2: Inversion Lens

For the core dependency identified in Stage 1:
1. State the default assumption about the core dependency.
2. Invert it: what if the core dependency were NOT satisfied / were replaced / were removed?
3. Trace consequences of the inversion.
4. Output: the **inversion insight** — what the inversion reveals about hidden constraints in P.

### Stage 3: Synthesis

Combine Stage 1 and Stage 2 into a **Dependency Inversion Verdict**:

```
Core Dependency: <from Stage 1>
Inversion Result: <from Stage 2>
Hidden Constraint: <what the inversion reveals>
Risk Score: <high/medium/low>
Action: <reframe P using the hidden constraint as the new anchor>
```

## Output Schema

```json
{
  "input": "<problem or skill under review>",
  "stage1_core_dependency": "<the dependency identified>",
  "stage2_inversion": "<the inversion applied to the core dependency>",
  "hidden_constraint": "<what the inversion reveals>",
  "risk_score": "high|medium|low",
  "reframe": "<restated problem using the hidden constraint as anchor>"
}
```

## Quality Gate

- [ ] Stage 1 identifies at least 1 dependency chain with at least 3 components
- [ ] Stage 2 inverts the core dependency (not a peripheral one)
- [ ] Hidden constraint is NOT the same as the stated problem
- [ ] Reframe is substantively different from the original input
- [ ] Risk score is justified by the analysis

## Usage

```bash
# Step 1: Read dependency_lens.md, apply Stage 1
# Step 2: Read inversion_lens.md, apply Stage 2 to the core dependency
# Step 3: Synthesize per Stage 3
```

## Why This Recipe Is Valuable

Most failure modes in skill crafting come from unexamined dependencies masquerading as design choices. This recipe exposes that class of bug by forcing the two lenses to interact rather than run in isolation. A skill that survives this pipeline is one where the agent has examined both what holds it together AND what would break it apart.
