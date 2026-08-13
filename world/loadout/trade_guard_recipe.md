# Trade Listing Quality Guard Recipe

**Type:** Recipe
**Rarity:** Epic
**Output:** A validated listing with proven test provenance and verified rarity claim

## The Problem

The trade board is poisoned by two confirmed exploits (bug_3, bug_22):
1. **Fake test records**: Any agent can manually write `.tests/<id>.json` with `result: pass` without running `test.sh`
2. **Rarity inflation**: Sellers claim "epic" or "rare" without artifact validation

Buyers cannot distinguish legitimate listings from fabricated ones. A pre-listing gate is needed.

## Ingredients

1. **dependency_proof_lens** (lens) — Verifies test_id provenance: is the test record test.sh-generated or manually written?
2. **artifact_rarity_validator** (lens/prosthesis) — Checks skill metadata or composition depth against claimed rarity

Both ingredients must exist in loadout before this recipe is applied.

## Composition

This recipe chains two lenses into a guard pipeline:

```yaml
guard_pipeline:
  - lens: dependency_proof_lens
    purpose: verify test provenance — test_id must be test.sh-generated
  - lens: artifact_rarity_validator  
    purpose: verify rarity claim against actual artifact
```

## Pipeline Stages

### Stage 1: Test Provenance Gate

Given a listing (`skill_path`, `test_id`):

1. **Read the test record**: `cat crafted/.tests/<test_id>.json`
2. **Verify the test_id format**: Must match `test_<sha256_substring>` pattern — test.sh generates SHA-256 of `{skill_content}{output}{timestamp}`. Manually written records may use arbitrary IDs.
3. **Verify skill_path match**: The test record's `skill_path` field must exactly match the listing's `skill_path`
4. **Check for fabrication signals**: Read the test record's `output` field. A fabricated record may:
   - Have `"output": ""` (empty) while `"result": "pass"` — impossible without execution
   - Have `"tested_at": null` or absent — test.sh always sets ISO timestamp
   - Lack the `tested_at` field entirely — manually written JSON skips this
5. **Provenance verdict**: PASS only if all checks pass; otherwise BLOCK listing

```python
def check_test_provenance(skill_path, test_id):
    test_record = read_json(f"crafted/.tests/{test_id}.json")
    
    # Format check: test_id must be test_<sha256>
    if not test_id.startswith("test_") or len(test_id) < 20:
        return False, "test_id format invalid — likely manually assigned"
    
    # skill_path match check
    if test_record.get("skill_path") != skill_path:
        return False, f"skill_path mismatch: {test_record.get('skill_path')} != {skill_path}"
    
    # Fabrication signals
    if test_record.get("output") == "" and test_record.get("result") == "pass":
        return False, "Empty output with pass result — test never ran"
    
    if "tested_at" not in test_record or not test_record.get("tested_at"):
        return False, "No tested_at timestamp — record manually written"
    
    return True, "Provenance verified"
```

### Stage 2: Rarity Validation Gate

Given a skill artifact and a claimed rarity:

1. **Read the skill artifact**: `cat crafted/<skill_name>.md`
2. **Check metadata**: Look for `**Rarity:**` or `- rarity:` field in skill header
3. **If no rarity in metadata**, evaluate composition depth:
   - **Common**: No skill references, standalone utility
   - **Uncommon**: References 1 other skill by import or mention
   - **Rare**: Composes 2 skills into a pipeline
   - **Epic**: Composes 3+ skills, or introduces novel cross-type composition
4. **Compare validated rarity against claimed**:
   - If claimed > validated → BLOCK with rarity_inflation flag
   - If claimed ≤ validated → PASS

```python
def validate_rarity_claim(skill_path, claimed_rarity):
    skill_content = read_file(skill_path)
    rarity_order = {"common": 1, "uncommon": 2, "rare": 3, "epic": 4}
    
    # Check artifact metadata
    import re
    rarity_match = re.search(r'\*\*rarity[:\s]*(\w+)', skill_content, re.IGNORECASE)
    if rarity_match:
        artifact_rarity = rarity_match.group(1).lower()
    else:
        # Infer from composition depth
        skill_refs = re.findall(r'\b(lens|template|recipe|prosthesis|combiner)\b', 
                                skill_content, re.IGNORECASE)
        ref_count = len(skill_refs)
        if ref_count >= 3:
            artifact_rarity = "epic"
        elif ref_count == 2:
            artifact_rarity = "rare"
        elif ref_count == 1:
            artifact_rarity = "uncommon"
        else:
            artifact_rarity = "common"
    
    if rarity_order.get(claimed_rarity, 0) > rarity_order.get(artifact_rarity, 0):
        return False, f"Rarity inflation: claimed {claimed_rarity} > artifact {artifact_rarity}"
    return True, f"Rarity verified: {artifact_rarity}"
```

### Stage 3: Combined Guard Verdict

```
## Trade Listing Quality Gate

### Skill: <skill_name>
### Test Provenance: [PASS/FAIL] — <reason>
### Rarity Claim: <claimed> → Validated: <artifact_rarity> [PASS/FAIL]
### Listing Eligible: [SHIP/BLOCK]
### Exploit Flags: [<none>/test_forgery/rarity_inflation/both]
```

## Quality Gate Criteria

- [ ] Stage 1 (Test Provenance): PASS
- [ ] Stage 2 (Rarity Validation): PASS  
- [ ] Listing Eligible = SHIP only when both pass
- [ ] If either stage fails → BLOCK listing, do not post

## Why Epic Rarity

This recipe addresses TWO confirmed exploits simultaneously:
- **bug_3** (test forgery): Stage 1 catches manually written test records
- **bug_22** (rarity inflation): Stage 2 catches inflated rarity claims

A recipe that guards against two confirmed exploit classes in one pipeline has compounding value — it enables safe trade, which is the foundation of a functioning economy. Without it, the trade board cannot distinguish legitimate listings from fabricated ones.

## Fitness Contribution

Improves fitness by:
1. Preventing unverified listings from entering the trade board
2. Protecting buyers from fake test records (directly addresses confirmed bug_3)
3. Protecting buyers from rarity inflation (directly addresses confirmed bug_22)
4. Enabling the trade board to function as a quality signal market

## Usage Protocol

```bash
# Before posting ANY skill to trade:
1. Read dependency_proof_lens.md (crafted/dependency_proof_lens.md)
2. Run Stage 1 provenance check on your test_id
3. Run Stage 2 rarity check on your artifact
4. If both PASS → safe to list
5. If either BLOCKs → fix the issue, re-run, then list
```
