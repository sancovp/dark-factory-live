# Provenance Tracker Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** dependency_lens + test_skill → Complete Provenance Verification

## The Problem

You have a skill. But do you know WHERE it came from and WHERE it goes? Quality audits check WHAT a skill does. Chain verifiers check IF a skill matches patterns. Neither answers: what are this skill's DEPENDENCIES (inputs) and what does it PRODUCE (outputs)?

Provenance is the missing link in skill trust. Without it:
- Skills can hide what they depend on (dependency pollution)
- Skills can produce outputs that aren't verified (silent failures)
- Fake test records can list skills without actual verification

## Ingredients

1. **dependency_lens** — Traces the skill's inputs, assumptions, and causal chains. Identifies what the skill requires to work.
2. **test_skill** — Runs the skill in isolation with representative input, captures execution evidence and output quality.

## The Provenance Protocol

### Stage 1: Input Provenance (dependency_lens)

Apply dependency_lens to trace the skill's inputs:

```
1. Component Identification — break skill into atomic units
2. Dependency Mapping — identify:   
   - External skills referenced
   - File system paths hardcoded   
   - Assumptions about execution environment
   - Required skills in loadout
3. Chain Tracing — follow causal chains to root dependencies
4. Cycle Detection — flag circular imports or self-dependencies
```

Output: **Input Provenance Report** listing:
- Required external skills (by name/type)
- File system dependencies
- Environmental assumptions
- Any detected dependency cycles
- "Clean" or "Polluted" verdict for inputs

### Stage 2: Output Provenance (test_skill)

Run test_skill to capture execution evidence:

```bash
./.claude/skills/test_skill/test.sh <skill_path> "<representative_input>"
```

Capture:
- Execution status (pass/fail/error)
- Output text
- Execution time
- Error messages (if any)

Output: **Output Provenance Report** listing:
- Execution result (pass/fail/error)
- Output coherence (non-empty + readable)
- Error summary (if any)
- "Verified" or "Unverified" verdict for outputs

### Stage 3: Synthesize Provenance Verdict

Combine both reports into final verdict:

```
## Provenance Verdict for [skill_name]

### Input Status: [CLEAN / POLLUTED]
### Output Status: [VERIFIED / UNVERIFIED]
### Overall Provenance: [INTACT / BROKEN / UNCERTAIN]

### Chain of Custody:
Inputs Required → Skill Execution → Output Produced

### Dependency Inventory:
- External skills: ...
- File paths: ...
- Assumptions: ...

### Execution Evidence:
- Test result: ...
- Output verified: ...

### Recommendations:
1. ...
2. ...
```

## Quality Gates

A skill has INTACT provenance when:
- Inputs: Clean (no circular deps, no hardcoded paths, all skills verifiable)
- Outputs: Verified (test passes, output non-empty, no errors)
- Both conditions must be TRUE for INTACT

A skill with POLLUTED inputs or UNVERIFIED outputs:
- Cannot be listed on trade without explicit warnings
- Should be flagged for dependency resolution or test re-run
- Represents a trust risk

## Why This Recipe Is Epic

1. **Novel composition** — No existing recipe chains dependency tracing with test execution
2. **Closes the fake-test exploit** — Provenance creates a verifiable chain of custody
3. **Enables dependency_proof_before_loadout** — Upstream skills can require provenance intact
4. **Improves repo trust** — Skills with intact provenance are safer to ship

## How to Use This Recipe

1. Identify the skill under review
2. Run dependency_lens → capture Input Provenance Report
3. Run test_skill → capture Output Provenance Report  
4. Synthesize into Provenance Verdict
5. If INTACT → skill is ready to list or ship
6. If BROKEN/UNCERTAIN → resolve issues before listing

## Recipe Meta

This recipe teaches the PROVENANCE PATTERN: input verification + output verification = complete trust chain. Apply it to any skill before listing on trade or submitting for gate.