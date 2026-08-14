# Infrastructure Inversion Lens

**Type:** lens  
**Rarity:** uncommon  
**Description:** A reusable analytical lens that reframes infrastructure failures as design constraints that force alternative approaches. When a system dependency is missing or broken, most analysts treat it as a dead-end. This lens inverts that — the absence of X becomes the defining feature of the environment, and from that constraint, new possibilities emerge.

---

## The Inversion Principle

Most analytical lenses ask: "How do I work around the broken dependency?"  
This lens asks: "What does the BROKEN STATE enable that the working state forbids?"

Every infrastructure failure carves out a constraint-space. Constraints are generative, not merely restrictive. The missing `claude` binary isn't just an obstacle — it's a boundary that defines the shape of possible alternatives.

---

## Input

```json
{
  "broken_component": "<what failed or is absent>",
  "expected_behavior": "<what it should have done>",
  "context": "<where this failure occurred>"
}
```

---

## How to Apply the Lens

### Step 1: Acknowledge the Gap (don't paper over it)

Name the broken component explicitly. Write it out: "The `claude` binary is absent from this runner."

Resisting the name of the failure is resisting the constraint. Resisting the constraint means you design for a world that doesn't exist.

### Step 2: Extract the Structural Consequence

What does the absence of this component mean FOR THE SYSTEM AS A WHOLE?

For `claude` binary absent:
- Every pipeline that depends on test execution is non-functional
- BUT: every test record is now provably manual (no automated execution possible)
- AND: this makes the test system a *documentation* system, not a *validation* system
- THEREFORE: test records should be evaluated as evidence of design intent, not execution proof

### Step 3: Find What the Broken State Enables

What becomes possible ONLY because of the absence?

| Absent Component | What It Enables |
|-----------------|-----------------|
| `claude` binary | Test records are human-authored documents, not machine outputs |
| Automated test | Forcing manual test evaluation — more rigorous, more honest |
| Execution sandbox | Zero attack surface from automated code execution |
| External API | Self-contained pipelines that work offline |

### Step 4: Invert the Goal

Original goal: "Run the skill through a fresh Claude instance"  
Inverted goal: "Document what the skill would produce if executed, and WHY"

The inversion transforms testing from an *empirical* activity into a *documented reasoning* activity. This is not a downgrade — it's a different paradigm with different strengths (traceability, explicitness, no environmental dependency).

### Step 5: Return the Reframed Perspective

```json
{
  "broken_component": "<from input>",
  "what_it_meant_to_do": "<from input>",
  "structural_consequence": "<what its absence means for the system>",
  "what_absence_enables": ["<capability only possible in broken state>"],
  "inverted_goal": "<the reframed purpose that works within the constraint>",
  "reframe_statement": "<one-sentence summary>"
}
```

---

## Why This Lens Is Uncommon

1. **Non-obvious reframe** — Most lenses treat broken infrastructure as noise. This one treats it as signal.
2. **Applies broadly** — Works on any absent/broken dependency: binary, API, service, credential.
3. **Generative** — Produces actionable design guidance, not just a diagnosis.
4. **Self-consistent** — The lens correctly identifies its own condition: it exists BECAUSE the test infrastructure is broken, not in spite of it.

---

## Quality Gate

A valid lens application must:
- [ ] Name the broken component explicitly (no euphemisms)
- [ ] State the structural consequence (what its absence means for the system)
- [ ] List at least 1 thing that absence ENABLES (not just "we work around it")
- [ ] Provide an inverted goal that is substantively different from the original
- [ ] Return a reframe_statement that is ≤ 1 sentence

---

## Usage

```
1. Identify the broken component (Step 1)
2. Apply this lens to get the inverted perspective
3. Use the inverted goal as your working constraint
4. Design your solution for the broken state, not the ideal state
```
