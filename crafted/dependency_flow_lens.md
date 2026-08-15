# Lens: Dependency Flow Lens
Type: Lens
Output Type: Rare

## Reframes
- "What's needed?" → "What's been PROVEN to exist?"
- "Will this work?" → "Has this passed the gate, not just its own check?"

## What It Does
Transforms dependency claims into proof chains. Before declaring "X depends on Y", this lens verifies:
1. Y exists in loadout
2. Y has been gate-proven (not just listed)
3. The dependency is explicitly imported, not assumed

Per dependency_proof_before_loadout: importing another component requires proof that component exists AND is loadout-proven BEFORE installation.

## Usage
1. When you see a skill reference another component, apply this lens
2. Ask: "Does the target exist? Has it survived its own gate?"
3. A dependency is ONLY proven if:
   - The component is in loadout
   - The component passed the gate (not just listed)
   - The import is explicit (not ambient)

## Input Triggers
- "This skill requires X"
- "Import from component"
- "Dependency on another skill"
- Any skill that imports, references, or composes others

## Output Shape
```
Dependency: [component name]
Existence Proof: EXISTS / NOT FOUND
Gate Status: GATE_PROVEN / STAGE_PROVEN / UNPROVEN / NOT_INSTALLED
Import Method: EXPLICIT / AMBIENT
Verdict: PROVEN / PROVISIONAL / BLOCKED
```

## Example
**Before Dependency Flow Lens:**
"This recipe composes the Causation Lens and Second-Order Lens."

**After Dependency Flow Lens:**
"This recipe composes:
- Causation Lens: EXISTS (crafted/causation_lens.md), GATE_STATUS unknown → BLOCKED until verified
- Second-Order Lens: EXISTS (crafted/second-order-lens.md), GATE_STATUS unknown → BLOCKED until verified

Verdict: PROVISIONAL — must verify gate status before claiming composition."

## When to Apply
- Before installing any skill that imports others
- Before shipping a composition claim
- During audit of dependency_proof_before_loadout compliance
- At the START of any skill that references another

## Quality Indicator
If your dependency check doesn't change your installation decision, you haven't applied the lens deeply enough. A lens that confirms what you already believe is decorative, not analytical.
