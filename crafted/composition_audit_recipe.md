# Recipe: Composition Audit Recipe
Type: Recipe
Output Type: Towering (Rare)
Yield: 1 audit skill that verifies a skill composition actually proves what it claims

## Problem This Solves
A composition that "passes internal stages" can still fail at the gate (per preflight_must_run_gate_criteria). This recipe audits whether a composition has been proven to survive its own gate — not just its own checks.

## Ingredients
1. Lens: Causation Lens (from causation_lens.md) — identifies whether quality improvements are actually CAUSED by the composition, not correlated with it
2. Lens: Second-Order Lens (from second-order-lens.md) — considers downstream effects of false-positive audit results
3. Gate Criteria Template (Common+) — a list of the actual gate requirements

## Assembly
### Step 1: Identify the Composition Under Audit
- Name the skill or recipe being audited
- Locate its test record (`.tests/*.json`)
- Note: Per audit_bug_exploit, test records can be fabricated — DO NOT trust the test record alone

### Step 2: Apply Causation Lens FIRST
Ask: "What would have happened WITHOUT this composition?"
- If throughput/fitness improved coincidentally, correlation ≠ causation
- If the same metric improved on other skills at the same time, suspect confound
- Identify the mechanism by which THIS composition causes improvement

### Step 3: Apply Second-Order Lens
Ask: "What happens if this audit misses a real failure?"
- False negative: A broken composition ships → damages codebase → degrades trust
- False positive: A valid composition reverts → wastes cycle → discourages composition
- Are audit failures worse than no audit?

### Step 4: Check Gate-Proof, Not Stage-Proof
The composition must prove it survives the ACTUAL GATE TEST, not:
- Internal checklist stages
- Self-declared validation
- Similar-looking assertions

Required proof elements:
1. The composition's output was tested against real gate criteria
2. The gate test ran end-to-end (not mocked)
3. The result was recorded in a way that could be independently verified

### Step 5: Apply Template
Fill in the audit report:
```
Composition: [name]
Gate Proof Status: PROVEN / UNPROVEN / PARTIAL

Mechanism (Causation Lens):
- How this composition causes improvement: [description]
- Confound check: [passed/failed]

Downstream Risk (Second-Order Lens):
- If wrong: [consequence]
- Acceptable risk level: [low/med/high]

Verdict: SHIP / HOLD / REVISE
```

## Quality Check
- Remove Causation Lens: Can you distinguish correlation from causation? (Must: no → lens is essential)
- Remove Second-Order Lens: Does the audit miss downstream failure modes? (Must: yes → lens is essential)
- Remove both: Is the audit defensible without considering cause and effect? (Must: no → combination creates value)

## Expected Rarity
Two lenses + one template → Rare (Towering if both lenses are Uncommon+)
The recipe transforms observation into proof by demanding causal mechanism and second-order consequences.

## Why This Recipe Works
Most audits check "did it pass?" — this recipe checks "did it prove the right thing?" A composition that passes its own tests but fails the gate is worse than no composition: it consumes cycle and gives false confidence. This recipe forces the audit to consider causation and consequences before declaring a composition ship-ready.

## Compliance with Standing Rules
- Satisfies audit_tool_also_needs_deps_proven: composition is audited before claiming to audit others
- Satisfies preflight_must_run_gate_criteria: forces gate criteria, not stage criteria
- Satisfies audit_valid_not_gate_valid: differentiates internal validation from gate passage
