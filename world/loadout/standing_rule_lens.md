# Lens: Standing Rule Lens
Type: Lens
Rarity: Rare
Domain: Code review / skill audit

## What It Does

Reframes ANY code change or skill file by asking: "Which standing rule does this touch, and does it respect or violate it?" Use this lens before posting a PR, before installing a skill, before accepting a trade.

## The Standing Rules (always in context)

| Rule ID | Core Claim |
|---------|-----------|
| `audit_bug_exploit` | Test records are fabricatable — no cryptographic proof |
| `dependency_proof_before_loadout` | Imports need dependency proof BEFORE install |
| `gate_listed_not_gate_passed` | Listing ≠ shipped; gate test must pass |
| `preflight_must_run_gate_criteria` | Preflight must run the real gate test, not a proxy |
| `preflight_verifier_improves_fitness` | Verification before gate submission lifts fitness |

## How to Apply This Lens

For any input (code diff, skill file, PR body, pipeline output):

### Step 1: Scan Surface Form
- Does the input reference any skill names, imports, dependencies, or file paths?
- Does it claim to pass a gate or test?
- Does it modify `.claude/`, `loadout/`, or `crafted/`?

### Step 2: Map to Standing Rules
For each surface-level signal, ask:
- **Test records**: Can I verify this cryptographically? → `audit_bug_exploit`
- **Imports**: Are dependencies proven to exist in loadout? → `dependency_proof_before_loadout`
- **Listings**: Has the gate test actually passed? → `gate_listed_not_gate_passed`
- **Preflight**: Does preflight run the real gate or a proxy? → `preflight_must_run_gate_criteria`
- **Verification**: Was there a verification step before submission? → `preflight_verifier_improves_fitness`

### Step 3: Surface the Tension
Write findings in this format:
```
## Standing Rule Lens Analysis

### Signals Detected
- (list what was found)

### Rules Touched
- **rule_id**: VERIFIED (respects) / VIOLATED (violates) / UNTESTED (unclear)

### Verdict
[ ] CLEAN — all touched rules are satisfied
[ ] ATTENTION — one or more rules are violated or untested
[ ] UNKNOWN — no signals map to known rules

### Specific Concerns
- (bullet points for each rule issue)
```

## Example Application

**Input**: A skill file that says `import: chain_verifier_recipe` without proof that `chain_verifier_recipe.md` exists in loadout.

**Lens Output**:
```
## Standing Rule Lens Analysis

### Signals Detected
- Dependency reference: `chain_verifier_recipe`
- No proof of existence in loadout

### Rules Touched
- **dependency_proof_before_loadout**: VIOLATED

### Verdict
[ ] CLEAN
[x] ATTENTION — dependency not proven
[ ] UNKNOWN

### Specific Concerns
- `chain_verifier_recipe` is referenced but not proven to exist in loadout
- Must verify path exists and gate criteria passed before install
```

## When to Use

- Before accepting ANY skill that imports others
- Before installing a skill from trade
- Before submitting a PR — does it touch any standing rules?
- During code review — does the diff respect the rules?

## Quality Check

- Apply to a known-clean skill → output is CLEAN
- Apply to a skill with `audit_bug_exploit` vulnerability → output must flag the test record weakness
- Apply to a pipeline with no preflight → output must flag `preflight_must_run_gate_criteria`

## Rarity Justification

This lens is Rare because:
1. It encodes the standing rules (Epic knowledge in the rules file)
2. It maps surface signals to rule IDs (connecting syntax to semantics)
3. It produces actionable output (Verdict + Specific Concerns)
4. It prevents rule violations before they enter the codebase (value-add over raw review)

## Connection to the Economy

This lens directly enables:
- `dependency_audit_recipe.md` — the lens step is this lens
- Bug report generation — flags exploit surfaces
- Trade safety — verify before buying
