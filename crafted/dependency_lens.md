# Dependency Lens
Type: Lens
Output Type: Rare

## Reframes
"Look at what this skill DOES → Look at what this skill REQUIRES"
"This skill exists → Does everything it needs exist too?"
"Installed → Proven to compose?"

## Purpose
Reframes skill evaluation from "what does it claim to do" to "does everything it depends on actually exist." Addresses the core failure mode: tools that find the right problem but fail their own gate (per audit_tool_also_needs_deps_proven).

## Application
When evaluating any skill that references other skills, components, or systems, apply this lens:

1. **Extract Dependencies**: What does this skill import, reference, or call?
2. **Verify Existence**: Do each of these dependencies exist in the loadout/target environment?
3. **Check Composition**: Does the skill's logic correctly use these dependencies, or does it assume they exist without proof?
4. **Reframe Failure**: A skill that identifies a gap in other skills must itself survive the same scrutiny — "correct diagnosis does not exempt a tool from its own gate."

## Input Triggers
- "This skill composes X and Y"
- "Install this lens to catch bugs"
- "Use this tool before deploying"
- Any skill claiming to verify, audit, or gate others

## Example Transformation
**Before Dependency Lens:**
"This pipeline recipe catches broken dependencies in other skills."

**After Dependency Lens:**
"This pipeline recipe catches broken dependencies IF its own dependencies (chain_verifier_recipe, etc.) exist and compose correctly. Does this skill have proof it passes its own test?"

## Quality Indicator
If the dependency check would FAIL for this skill itself, the skill cannot be trusted to evaluate others. The lens must apply symmetrically — if you wouldn't pass your own audit, you cannot conduct audits.

## Second-Order Warning
Tools that fail their own composition check but still surface bugs cause more damage than no tool: they consume loadout slots, give false confidence, and revert the finder along with the found.
