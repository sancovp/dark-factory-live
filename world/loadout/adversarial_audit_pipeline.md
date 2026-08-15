# Adversarial Audit Pipeline Recipe

**Type:** Recipe  
**Rarity:** Rare  
**Composes:** adversarial_lens + audit_lens → Adversarial Audit Pipeline

## The Problem

A skill might pass a standard audit but still contain hidden adversarial vectors — inputs crafted to exploit implicit assumptions. Standard audits verify correctness; adversarial audits verify robustness against misuse. This pipeline composes both into a single evaluation flow.

## Ingredients

1. **Adversarial Lens** (`crafted/adversarial_lens.md`) — Find inputs that break the skill's implicit contract
2. **Audit Lens** (`crafted/audit_lens.md`) — Verify the skill's artifact quality and documentation

## Pipeline Stages

### Stage 1: Adversarial Probe (via adversarial_lens)

For the skill under evaluation:
1. Identify the SKILL'S ASSUMED INPUT DOMAIN (what inputs does it expect?)
2. List EDGE CASES the skill does NOT explicitly handle
3. For each edge case, determine: would the skill silently fail, crash, or produce misleading output?
4. Construct at least 3 adversarial probes

Output: **Adversarial Probe Report** listing failure modes with severity scores (low/med/high/critical)

### Stage 2: Audit Verification (via audit_lens)

For each adversarial failure mode found in Stage 1:
1. Check if the skill's documentation acknowledges the edge case
2. Verify the artifact structure: does it have required sections?
3. Validate type consistency between description and code
4. Check for test coverage of adversarial inputs

Output: **Audit Verification Report** listing documentation gaps and structural weaknesses

### Stage 3: Synthesis

Combine Stage 1 and Stage 2 reports into a final verdict:

```
## Adversarial Audit Verdict for [skill_name]

### Adversarial Risk Level: [LOW/MEDIUM/HIGH/CRITICAL]
### Audit Gaps: N
### Combined Risk Score: X/10
### Verdict: [SAFE/WARNING/DANGER]
### Recommendations:
1. ...
2. ...
```

## Quality Gates

A complete pipeline must produce:
- At least 3 adversarial probes from Stage 1
- At least 2 documentation gaps from Stage 2
- A combined risk score with explicit reasoning
- At least 2 actionable recommendations

## Why This Is Rare

Most audit recipes apply one lens. Composing adversarial + audit into a pipeline catches:
1. Skills that are structurally correct but adversarially fragile
2. Skills with good documentation that still have hidden failure modes
3. Skills that pass standard tests but fail under novel inputs

The combination is non-obvious: adversarial thinking and audit thinking are different cognitive modes, rarely composed intentionally.
