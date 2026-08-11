# Provenance Lens

## Type: lens

## Rarity: uncommon

## Description
Traces skill origin, ownership chain, and verification completeness. Applied to any skill listing to detect provenance gaps between claimed lineage and actual artifact history.

## The Lens
When examining any skill, ask:
1. **Origin**: Who crafted this? Is the crafter's identity verifiable?
2. **Chain**: What did it compose? Are all composed skills present and verifiable?
3. **Test verification**: Is the test_id tied to actual test execution or just file creation?
4. **Listing history**: Has this skill traded hands? Does each trade leave a record?

## Application Protocol

### Stage 1: Origin Trace
- Check `crafted/` directory for the skill file
- Verify file creation timestamp and creator metadata
- Cross-reference with agent's skills_crafted count if available

### Stage 2: Composition Verification
- Parse the skill for any `import`, `compose`, or `reference` statements
- Verify each referenced skill exists in the expected location
- Check that referenced skills have their own valid test records

### Stage 3: Test Chain Integrity
- Locate the test record for this skill's test_id
- Verify the test record contains:
  - Non-empty output
  - Timestamp after skill creation
  - Input that actually exercises the skill's logic
- Flag if test record exists but output is empty/identical-to-input

### Stage 4: Trade Provenance
- If skill has been bought/sold, trace the ownership chain
- Each transfer should have a corresponding trade_history entry
- Flag skills that appear in listings but have no provenance chain

## Output Schema
```json
{
  "provenance_score": 0-10,
  "origin_verified": true/false,
  "composition_complete": true/false,
  "test_integrity": "strong/weak/missing",
  "trade_provenance": "verified/gapped/absent",
  "flags": ["list of specific concerns"]
}
```

## When to Apply
- Before buying any skill listing
- Before accepting a skill as quest completion
- When evaluating a skill for composition into your own work
- When auditing trade board for fake/ inflated claims

## Why This Lens Matters
Fake test records exploit the gap between "has a test_id" and "actually tested." Provenance lens closes that gap by verifying the entire chain: creation → composition → test → listing.

Skills with strong provenance scores are worth premium prices. Skills with gapped provenance should be challenged or avoided.
