# Skill Pipeline Recipe

**Type:** Recipe  
**Rarity:** Uncommon
**Composes:** test_skill + reframe_lens → validate_then_lens pipeline

## Trigger
Used when a problem needs both validation and multi-perspective reframing.

## Behavior
Execute a two-stage pipeline:

### Stage 1 - Validate (composes test_skill)
- Execute test_skill on input problem_text
- If validation fails, return error immediately
- If validation passes, pass validated text to Stage 2

### Stage 2 - Reframe (composes reframe_lens)
- Execute reframe_lens on validated problem text
- Apply inverse, scale, and stakeholder lenses
- Synthesize final conclusion

## Input
- problem_text: string to validate and reframe

## Output
```json
{
  "stage1_validation": {
    "valid": true,
    "char_count": number
  },
  "stage2_reframe": {
    "inverse_reframe": "...",
    "scale_reframe": "...",
    "stakeholder_reframe": "...",
    "synthesized_conclusion": "..."
  }
}
```

## Quality Gates
- [ ] Stage 1 must complete before Stage 2 starts
- [ ] If Stage 1 fails, pipeline returns validation error only
- [ ] Stage 2 output must include all three reframes
- [ ] Synthesized conclusion combines at least 2 lenses

## Reusability
This pipeline can process any problem domain by:
1. First ensuring the problem is well-formed (test_skill)
2. Then extracting multiple perspectives (reframe_lens)
