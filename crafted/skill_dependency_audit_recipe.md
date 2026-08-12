# Recipe: Skill Dependency Audit Recipe
## Type: recipe

## Composition
Chains three skills in sequence to audit a skill's dependency claims:
1. **causation_lens** — validates that a skill's stated dependencies have causal backing (not just co-occurrence)
2. **risk_inversion_lens** — inverts dependency assumptions to find hidden coupling risks
3. **second-order-lens** — traces second-order effects when dependencies are missing or violated

## Pipeline Logic
```
input_skill_path
  → causation_lens (validate: does dep X cause the claimed effect?)
  → risk_inversion_lens (invert: what risks does this dependency create?)
  → second-order-lens (propagate: what happens downstream if this dep fails?)
  → output: dependency audit report with risk ratings
```

## Inputs
- `input_skill_path`: path to skill to audit for dependency gaps

## When to Use
- Before installing any skill that imports or references other components
- When composing new recipes from existing skills
- During preflight checks per `dependency_proof_before_loadout` rule
- To detect the test-record fabrication exploit (skills claiming test deps that don't exist)

## Audit Steps

### Step 1: Apply Causation Lens
For each dependency claimed by the skill:
- Ask: "What causal mechanism connects dep X to the skill's output?"
- Ask: "Does dep X's absence BREAK the skill, or just change it?"
- Mark: CAUSAL (absence breaks) vs CORRELATED (absence merely changes)
- Flag: Any dependency marked CORRELATED should be questioned

### Step 2: Apply Risk Inversion Lens
For each CAUSAL dependency:
- Ask: "What is the hidden RISK in this dependency?"
- Ask: "What single point of failure does this create?"
- Ask: "What would happen if this dependency was compromised or absent?"
- Mark: RISK_RATING (low/med/high/critical)
- Flag: Any CRITICAL dependency without fallback is a loadout gap

### Step 3: Apply Second-Order Lens
For each flagged dependency:
- Ask: "If this dependency fails, what fails downstream?"
- Ask: "Who depends on THIS skill that would be affected?"
- Ask: "Is there a cascade risk?"
- Mark: CASCADE_RISK (none/possible/cascade)
- Flag: Any CASCADE_RISK requires a mitigation strategy

## Output Shape
```markdown
# Dependency Audit Report: {skill_name}

## Dependencies Audited
| Dep | Type | Risk | Cascade | Status |
|-----|------|------|---------|--------|
| dep_a | CAUSAL | HIGH | none | VERIFIED |
| dep_b | CORRELATED | LOW | possible | VERIFY_MECHANISM |
| dep_c | CAUSAL | CRITICAL | cascade | MISSING_GUARD |

## Findings
- **MISSING_GUARD**: dep_c has no fallback if unavailable
- **VERIFY_MECHANISM**: dep_b correlation not proven causal

## Recommendations
1. Install fallback for dep_c before loadout
2. Prove mechanism for dep_b or remove dependency claim

## Exploit Detection
- Test records claiming to test dep_c but no actual test exists
- Imports referencing skills not in loadout
- Composition claims without composition verification
```

## Quality Gates
This recipe passes its own audit when:
1. All three component lenses are present in loadout
2. Output follows the Dependency Audit Report shape
3. At least one dependency is flagged for review (otherwise the lens composition is wasted)

## Rarity: rare
*Composes 3 existing lenses → rare output per meta-composition rules*

## Addresses
- `dependency_proof_before_loadout` — verifies deps exist before install
- `audit_bug_exploit` — detects fabricated test records claiming false deps
- `dependency_gatekeeper_recipe` failure mode — provides the missing lens composition
