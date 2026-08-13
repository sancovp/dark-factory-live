# Dependency-Reframe Pipeline Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** dependency_lens + reframe_lens → Systematic Problem Decomposer

## The Problem

Most agents solve problems at the surface level — they see the stated problem and reach for the obvious solution. The Dependency-Reframe Pipeline breaks the problem down to its atomic components first, then applies reframing to each component individually. This produces problem statements that survive both structural and perspectival scrutiny.

## Why Epic

Two uncommon/rare lenses combine into a pipeline that is qualitatively different from either alone:
- **dependency_lens** extracts the hidden structure (components, relationships, root causes)
- **reframe_lens** transforms each structural element through inverse/scale/stakeholder lenses
- The composition = structural analysis → multi-perspective reframe → synthesized output

Most agents would use one lens or apply reframe to the whole problem. This pipeline systematically decomposes first, then reframes each piece.

## Ingredients

1. **dependency_lens** (`crafted/dependency_lens.md`) — Decomposes problems into atomic components and maps their relationships
2. **reframe_lens** (`crafted/reframe_lens.md`) — Applies inverse/scale/stakeholder perspective shifts to each component

## Pipeline

### Stage 1: Dependency Decomposition (via dependency_lens)

Input: problem_text  
Output: Structured dependency graph with components, relationships, root causes

```
1. Break problem into atomic components
2. Map inputs/outputs between components
3. Trace dependency chains to root causes
4. Detect any cycles or feedback loops
5. Return ranked list of components by criticality
```

### Stage 2: Multi-Perspective Reframe (via reframe_lens)

For each component from Stage 1, apply reframe_lens:

- **Inverse:** What if the opposite were true for this component?
- **Scale:** At what scale does this component behave differently?
- **Stakeholder:** Who benefits/loses from this component's role?

Output: Reframed problem statement with three observations per component

### Stage 3: Synthesis

Combine Stage 1 (structural decomposition) with Stage 2 (reframe per component):

```json
{
  "original_problem": "<input>",
  "components_identified": [{"name": "...", "criticality": "high/med/low", "relationships": [...]}],
  "refarmed_components": [{"component": "...", "inverse": "...", "scale": "...", "stakeholder": "..."}],
  "final_reframe": "<synthesized problem statement surviving both structural and perspectival analysis>",
  "abandoned_components": ["<why each low-criticality component was deprioritized>"]
}
```

## Quality Gate

- [ ] Stage 1 identifies at least 3 atomic components
- [ ] Stage 2 generates inverse/scale/stakeholder reframe for each component
- [ ] Final reframe is substantively different from the original problem
- [ ] Component criticality is justified (not arbitrary ranking)

## Example Application

**Input:** "How to make agents test more skills?"  
**Stage 1:** Components = test_runner, skill_repository, test_suite, agent_incentive. Relationships: agent_incentive → test_runner → test_suite → skill_repository. Root cause: agent_incentive (no reward for testing).  
**Stage 2:**  
- inverse: "What if testing was penalized?" → agents avoid it  
- scale: "Individual testing vs collective test coverage" → mismatch in incentives  
- stakeholder: "Buyers want tested skills; sellers are not rewarded for tests" → broken market signal  
**Final reframe:** "How do we make skill testing a reward-generating activity for agents, not just a cost?"  
**Contrast with naive approach:** The naive approach would say "add a testing requirement." The pipeline discovered the ROOT CAUSE (incentive misalignment) and reframed to an incentive design problem.

## Why This Is Better Than the Obvious Approach

The obvious approach to any problem is to solve it at face value. The Dependency-Reframe Pipeline forces structural decomposition first, ensuring reframes are grounded in actual components rather than surface language.
