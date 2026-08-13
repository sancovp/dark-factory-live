# Recipe: Compositional Audit Pipeline
Type: Recipe
Output Type: Rare
Yield: 1 audit skill that verifies skills actually compose their claimed dependencies

## Ingredients (Composition Chain)
1. **causation_lens** — identifies what mechanism produces the skill's output
2. **second-order-lens** — surfaces second and third-order failure modes

## Assembly
1. **Parse the target skill** — extract `Type:`, listed ingredients/skills, and claimed output
2. **Apply causation_lens FIRST**: "What causal mechanism connects the inputs to the claimed output?"
   - If no mechanism exists → skill is non-compositional (decorative only)
   - If mechanism exists but depends on skills not listed → composition incomplete
3. **Apply second-order-lens**: "What fails after this skill ships? What fails after THAT?"
   - Surface deployment failures
   - Surface dependency chain failures
   - Identify hidden assumptions
4. **Verify the composition**: check that listed ingredients actually exist in loadout or are properly stubbed
5. **Generate audit report** with:
   - `[COMPOSITIONAL]` if mechanism chain is complete
   - `[INCOMPLETE]` if deps missing or mechanism gaps exist
   - `[DECORATIVE]` if no real composition (just labels)

## Input Triggers
- "audit skill composition"
- "verify recipe completeness"
- "check dependency chain"

## Output Shape
```
Skill: <name>
Type: <type>
Composition Check:
  - Mechanism: <exists|missing>
  - Dependencies: <listed + verified|missing deps>
  - Second-order risks: <list>
  - Third-order risks: <list>
Verdict: [COMPOSITIONAL|INCOMPLETE|DECORATIVE]
```

## Quality Gate
This recipe passes the gate ONLY if:
1. Both component lenses exist and are referenced by name
2. The output format matches the schema above
3. A test exists that verifies actual composition vs label-only

## Rarity: rare
Composition: causation_lens + second-order-lens → rare output (lens pipeline)

## Example
**Input:** lens_verify_pipeline.md
**Causation check:** Pipeline chains verifier → lens. Mechanism: validate THEN reframe. Exists.
**Second-order:** What fails? Verification passes but lens misfires. What fails after? Wrong reframing guides wrong analysis.
**Verdict:** [COMPOSITIONAL]
