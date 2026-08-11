# Recipe: Root Cause Cascade
Type: Recipe
Output Type: Rare
Yield: 1 analysis skill that traces causal chains through multiple layers to find the true origin of problems

## Composed Skills
This recipe COMPOSES two existing analytical lenses:
1. **Causation Lens** (crafted/causation_lens.md) — transforms correlations into causal hypotheses with mechanism identification
2. **Second-Order Lens** (crafted/second-order-lens.md) — forces consideration of consequences of consequences

## Assembly Instructions

### Phase 1: Surface → Causal (Apply Causation Lens)
1. Start with a symptom or problem ("X is broken")
2. Ask: "What mechanism could produce this?"
3. Ask: "What had to change for X to break now?"
4. Generate 3-5 causal hypotheses

### Phase 2: Layer → Deep (Apply Second-Order Lens to Each Hypothesis)
For EACH hypothesis from Phase 1:
1. **Immediate**: What directly causes this cause?
2. **First-Order**: What response does this cause trigger?
3. **Second-Order**: What response to that response occurs?
4. **Root Candidate**: Does this chain terminate in something you can actually control?

### Phase 3: Convergence
1. Map all causal chains side-by-side
2. Find where multiple chains converge = likely root cause
3. Flag any chain with no controllable root = systemic problem

### Phase 4: Actionability Filter
- Root cause controllable? → Actionable fix
- Root cause systemic? → Flag for structural change
- Multiple root candidates? → Rank by leverage (fix this, prevents most downstream)

## Quality Gates
- Each chain must terminate at a controllable factor or a clearly-flagged systemic one
- Must identify at least 1 convergence point across chains
- If all chains terminate at "management decision" without specifics → REJECT and restart

## Example Application
**Symptom**: "Tests are flaky in CI"
- Causation Lens → mechanism hypotheses: timing sensitivity, shared state, async race conditions
- Second-Order on each → surface cause → what enabled it → what enabled that
- Convergence: all chains converge on "no flaky test ownership" + "test suite too large to review"
- Actionable: assign test owners, split large suite

## Why This Recipe Works
Causation Lens finds causes. Second-Order Lens prevents stopping too early. Together they prevent both "correlation is causation" AND "stopping at the first cause" mistakes.

## Rarity Assessment
- Composes 2 Common lenses → Rare output
- Both lenses are tested and proven
- Novel composition creates emergent capability neither lens has alone
