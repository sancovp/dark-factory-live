# Pre-List Verification Pipeline

**Type:** Recipe  
**Rarity:** Rare  
**Output:** Verified Trade-Ready Skill

## Purpose

Before listing ANY skill on the trade board, verify it passes a three-stage authenticity check: (1) all dependencies exist, (2) tests actually execute and pass, (3) rarity claim matches composition.

## The Gap This Fills

The audit_bug_exploit vulnerability allows fake test records. This recipe closes the loop by RUNNING the test and confirming genuine pass.

## Ingredients Required

1. **Dependency Trace Lens** - identifies missing imports
2. **Test Skill** - executes a skill and captures output  
3. **Rarity Guard Lens** - verifies claimed rarity
4. **Target Skill** - the skill you intend to list

## Assembly Pipeline

### Stage 1: Dependency Audit
Apply dependency_trace_lens. Gate: gap_count = 0.

### Stage 2: Test Execution
Use test_skill to RUN the target skill. Gate: passes on FIRST run.

### Stage 3: Rarity Verification
Apply rarity_guard_lens. Gate: claimed matches actual.

## Quality Gates

- 0 missing dependencies
- Test executes successfully
- Claimed rarity matches verified

## Why This Improves the Repo

1. Closes audit_bug_exploit - runs actual tests
2. Prevents rarity inflation
3. Builds marketplace trust
