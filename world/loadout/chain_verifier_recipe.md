# Chain Verifier Recipe

**Type:** Recipe  
**Rarity:** Rare  
**Composes:** meta_pe_lens → Skill Quality Verifier

## The Problem

You have skills. But do they work? Will they pass the gate? Can they be trusted in a pipeline? This recipe answers those questions by applying the Meta-PE Lens to any skill, producing a quality verdict.

## Ingredients

1. **meta_pe_lens** — Systematic evaluation via Provenance, Failure Modes, Type, Novelty, and Composition checks.

## The Chain Protocol

### Apply Meta-PE Lens

Take the skill under evaluation and apply the Meta-PE Lens questions:

**1. PROVENANCE Check**
- Is the output grounded in the provided input, or generated from training?
- Can you trace each claim back to a source in the input?

**2. FAILURE MODES Check**
- What would make this fail?
- What edge cases are unhandled?
- If someone used this wrong, what breaks?

**3. TYPE CHECK**
- Does the output match what the TYPE promises?
- If it's a "recipe", does it actually compose other things?

**4. NOVELTY Check**
- Would a default prompt produce the same output?
- Is there anything unique or non-obvious here?

**5. COMPOSITION Check**
- If it references other skills/tools, do those exist?
- Are dependencies listed and verifiable?

### Synthesize

Combine all checks into a **Chain Verdict**:

```
## Chain Verdict for [skill_name]

### Provenance Score: X/5
### Failure Modes Score: X/5
### Type Check Score: X/5
### Novelty Score: X/5
### Composition Score: X/5
### Overall: [PASS/REVIEW/REJECT]
### Recommendations:
1. ...
```

## Quality Gates

A skill VERDICT must include:
- Scores for all 5 dimensions
- Specific evidence for each score
- At least 2 actionable recommendations
- Final PASS/REVIEW/REJECT determination

## Why This Recipe Improves the Repo

The Meta-PE Lens catches what looks valid but isn't:
1. Catches fake test records (Composition fails)
2. Catches unrealized skills (Type check fails)
3. Standardizes quality across the economy
