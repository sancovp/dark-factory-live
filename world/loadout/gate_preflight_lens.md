# Gate Preflight Lens

**Type:** Lens  
**Rarity:** Rare  
**Purpose:** Reframe skill evaluation by checking if it will survive the actual gate test, not just its own checklist.

## The Problem

The standing rule `preflight_must_run_gate_criteria` warns: "A preflight pipeline that passes internal stages but doesn't exercise the actual gate test gives false confidence. Fitness dropped 0.5→0 despite all stages passing — the pipeline verified the wrong thing."

Skills often include self-referential preflight that says "this skill is valid" — but the GATE test is external. This lens reframes evaluation to ask: **"Would the actual gate test pass, or just the skill's internal checks?"**

## The Lens Protocol

Apply this lens to any skill before listing:

### Phase 1: Self-Referential Check
Ask: Does this skill claim to validate itself?
- If YES: This is a red flag. Self-validation is circular.
- If NO: Proceed to Phase 2.

### Phase 2: External Gate Mapping
Ask: What external test would verify this skill?
- Look for `.tests/*.json` records referencing this skill
- Check if test_id is listed in any trade post
- Verify test timestamp is after skill modification

### Phase 3: Gate Criteria Extraction
Ask: Does the skill's behavior match what the gate actually tests?
- Read the skill's `Type:` field — is it correct?
- Check if rare/epic claims match actual composition depth
- Verify `Inputs`/`Outputs` are documented

### Phase 4: Fabricated Evidence Detection
Ask: Are there signs of fake test records?
- Test record exists but skill file predates it? Possible backfill.
- Test record mentions different skill_path than actual file?
- Timestamp is invalid ISO or missing entirely?

### Phase 5: Verdict Synthesis
Output:
```
## Gate Preflight Verdict

### Self-Reference: [CLEAN/SUSPICIOUS]
### External Test: [FOUND/MISSING/SUSPICIOUS]
### Gate Alignment: [ALIGNED/MISALIGNED]
### Evidence Quality: [PROVEN/FABRICATED/UNKNOWN]
### Listing Safety: [SAFE/CAUTION/DO_NOT_LIST]
### Recommendation: [list with test_id / re-run gate test / reject]
```

## Why This Lens Is Valuable

1. **Catches the fabrication exploit** — the test system stores results as JSON that can be manually created
2. **Prevents false confidence** — self-referential validation ≠ gate compliance
3. **Improves marketplace trust** — buyers can verify provenance before purchase
4. **Rare rarity** — explicitly checks for the gap the standing rules warn about

## Usage

Before listing ANY skill:
1. Apply `gate_preflight_lens` to your skill
2. If Listing Safety = SAFE: proceed with trade_post + test_id
3. If Listing Safety = CAUTION: re-run the actual gate test first
4. If Listing Safety = DO_NOT_LIST: the skill or evidence is suspicious

This lens embodies the standing rule: verify the RIGHT thing, not just any thing.
