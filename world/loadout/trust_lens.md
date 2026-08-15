# Trust Lens

**Type:** Lens  
**Rarity:** Rare  
**Purpose:** Detect hidden trust dependencies in skills, identify when trust is assumed rather than earned.

## The Reframe

Every skill makes implicit trust claims:
- "This skill works as advertised" (capability trust)
- "This skill won't harm your system" (safety trust)  
- "This skill's output can be verified" (verifiability trust)

Most skills never state these assumptions. The Trust Lens surfaces them.

## Questions to Ask

When examining any skill, ask:

1. **Capability Trust**: What does this skill ASSUME about the input? What happens if assumptions are violated?
   
2. **Safety Trust**: Does this skill modify state? Could it corrupt data or create side effects?
   
3. **Verifiability Trust**: Can the output be independently verified? Or must you trust the skill blindly?

4. **Provenance Trust**: Where did this skill come from? Who tested it? What evidence exists?

5. **Reversibility Trust**: If this skill causes harm, can it be undone?

## Red Flags

- Skill assumes valid input without validation
- Skill modifies files without backup
- Skill output is a single binary (pass/fail) with no intermediate verification
- Skill references other skills but doesn't prove they exist
- Test record exists but test itself wasn't run (audit_bug_exploit)

## The Reframe Output

```json
{
  "skill_path": "<examined skill>",
  "trust_assumptions": {
    "capability": "<what's assumed about input>",
    "safety": "<what's assumed about side effects>",
    "verifiability": "<how output can/cannot be verified>",
    "provenance": "<what's known about skill origin>",
    "reversibility": "<what happens if this fails>"
  },
  "trust_score": "0-10",
  "red_flags": ["..."],
  "recommendation": "USE WITH CAUTION / SAFE TO USE / DO NOT USE"
}
```

## Why This Improves the Repo

The fake test exploit thrives in low-trust environments. The Trust Lens gives buyers a structured way to evaluate skills BEFORE purchasing, reducing demand for fraudulent listings.
