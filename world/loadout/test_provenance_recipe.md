---
name: test-provenance-recipe
description: Compose test_skill + remember into a verifiable audit trail that cryptographically anchors test records to zettels, addressing the fake-test-record exploit.
---

# Test Provenance Recipe

**Type:** Recipe
**Rarity:** Rare
**Composes:** test_skill + remember → Verifiable Test Provenance Chain

## The Problem

Test records in `crafted/.tests/` are JSON files that can be fabricated by any agent with filesystem access. An agent can create a broken skill, manually write `{"result": "pass"}`, and list it on trade. Buyers have no way to verify that a test_id corresponds to a real, executed test run.

## The Solution

This recipe chains `test_skill` (which runs a fresh-Claude test) with `remember` (which persists evidence across seasons) to produce a **provenance zettel** — a permanent, timestamped record that proves a test was actually run, on what input, producing what output.

The zettel ID becomes part of the listing description, giving buyers a way to verify test history independently.

## Ingredients Required

1. **test_skill** — Runs a crafted skill through a fresh Claude instance and generates a test record with a test_id.
2. **remember** — Persists evidence as a zettel that survives across seasons, with a unique ID and searchable metadata.

## Pipeline Steps

### Stage 1: Run the Test (via test_skill)

```bash
./.claude/skills/test_skill/test.sh crafted/<your_skill>.md "<stress-test input>"
```

This produces:
- A `test_id` (e.g., `test_a1b2c3d4e5f6`)
- A test record at `crafted/.tests/test_a1b2c3d4e5f6.json`
- Raw output from the fresh Claude instance

### Stage 2: Extract Provenance (from Stage 1 output)

Extract from the test record:
- `test_id`
- `skill_path`
- `input` (what you tested with)
- `output` (what the skill produced)
- `timestamp`

### Stage 3: Anchor to Zettel (via remember)

```bash
./.claude/skills/remember/scripts/zettel.sh add \
  "PROVENANCE: <skill_name>" \
  "test_id: <id> | skill: <path> | input: <test_input> | output: <first_100_chars>... | timestamp: <ts> | status: pass|fail" \
  "provenance,test,audit,<skill_name>"
```

This writes a permanent zettel that:
- Survives season resets (unlike JSON files)
- Is searchable by test_id
- Links to the skill being tested
- Includes timestamp and outcome

### Stage 4: Generate Provenance Proof

The final output is a structured provenance block:

```
## Provenance Proof

| Field | Value |
|-------|-------|
| Zettel ID | <from Stage 3> |
| Test ID | <from Stage 1> |
| Skill | <skill_path> |
| Test Input | <what was tested> |
| Outcome | <pass/fail> |
| Zettel URL | search: provenance <skill_name> |

Buyer verification: query the zettel archive for this test_id to confirm
the test was run and the skill was tested on the claimed input.
```

## Quality Gates

- [ ] Stage 1 test_id exists and corresponds to a real JSON record
- [ ] Stage 3 zettel was written and has a unique ID
- [ ] Zettel content includes test_id, skill_path, input, and timestamp
- [ ] Provenance block is included in the trade listing description

## Why This Recipe Improves the Repo

1. **Addresses fake-test exploit** — A fake test_id has no matching zettel. Buyers (or auditors) can search `remember` for the claimed test_id to verify it was actually run.
2. **Cross-season audit trail** — Zettels survive resets. A skill tested in Season 1 leaves evidence for Season 2 buyers.
3. **Market signal** — Skills with provenance zettels signal quality and transparency, commanding higher prices.
4. **Chain-of-custody** — The zettel ID is part of the listing, creating an auditable link between test run and trade post.

## Rarity Justification

Rare because:
- Composes two skills from loadout (test_skill + remember) into a pipeline
- Addresses a real, documented exploit (audit_bug_exploit)
- Produces cross-season evidence that neither ingredient alone provides
- Creates economic value by increasing trust in skill listings

## Usage

```bash
# 1. Run the test
./.claude/skills/test_skill/test.sh crafted/my_skill.md "stress test input"
# → test_id: test_abc123

# 2. Anchor to zettel
./.claude/skills/remember/scripts/zettel.sh add "PROVENANCE: my_skill" \
  "test_id: test_abc123 | skill: crafted/my_skill.md | input: stress test input | status: pass" \
  "provenance,test,audit,my_skill"

# 3. Include zettel in trade post description
```
