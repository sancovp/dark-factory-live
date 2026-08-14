# Interface Contract Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Reframes code analysis by examining component interfaces and implicit contracts

## The Lens Perspective

When examining code, most agents see functions, classes, and data structures. This lens shifts attention to **where components meet** — the interfaces, boundaries, and implicit contracts that define how pieces communicate.

## How to Apply

For any code artifact under review:

### Step 1: Map the Boundaries

Identify every place where one component touches another:
- Function calls across modules
- Data passed between structures  
- Shared state mutations
- Configuration consumed by code

### Step 2: Surface the Contracts

For each boundary, ask:
- **Input contract**: What does this interface PROMISE to receive? (types, formats, preconditions)
- **Output contract**: What does it GUARANTEES to produce? (return values, side effects)
- **Assumption contract**: What does it ASSUMES without verifying? (null checks, auth state, etc.)

### Step 3: Find the Gaps

The lens reveals problems where:
- Contracts are **unspoken** (no documentation, types, or validation)
- Contracts **contradict** (caller expects X, callee expects Y)
- Contracts **leak** (internal state exposed beyond boundary)

### Step 4: Reframe the Problem

Instead of "how do I fix this bug?" ask:
- "What contract is broken here?"
- "Where did the assumption originate?"
- "Should this boundary enforce the contract?"

## Output Template

```
## Interface Contract Analysis

### Boundaries Found: N
### Contracts Surfaced:
1. [boundary] → Input: X | Output: Y | Assumptions: Z
2. ...

### Gaps Identified:
1. [gap type] at [boundary]: [description]
2. ...

### Reframed Problem:
[Restated question using contract language]
```

## Quality Gate

A valid lens output must:
- Identify at least 3 distinct boundaries
- Surface at least 2 implicit contracts
- Document at least 1 assumption that could fail
- Provide a reframed question in contract terms

## Why This Lens Improves the Repo

By shifting analysis from "what does this code do?" to "what does this interface promise?", agents find:
- Missing input validation at boundaries
- Undocumented assumptions that cause bugs
- Opportunities to add contracts that prevent future failures
- Clearer refactoring targets (strengthen the contract, not the implementation)
