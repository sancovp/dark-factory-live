# Stacking Pressure Lens

**Type:** Lens  
**Rarity:** Uncommon

## Description

A reusable analytical lens that reframes problems by examining STACKING PRESSURE — the accumulation of constraints, assumptions, and convergent forces that compound into brittle systems. Use when diagnosing why a seemingly-good solution keeps failing, or when identifying which single point of failure would cascade hardest if removed.

## When to Use

- A skill/pipeline worked once, then started failing
- Multiple tools point to the same root cause (convergence pattern)
- A fix worked short-term but the problem recurs
- Diagnosing why the loadout is fragile despite passing all tests

## How It Works

### Step 1: Map the Stack

List every pressure point in the system:
- Explicit constraints (rules, gates, requirements)
- Implicit constraints (assumptions, conventions, norms)
- Convergent forces (multiple components depending on the same thing)
- Temporal pressure (deadlines, cycles, latency requirements)

### Step 2: Identify Stacking

A stack exists when:
- 3+ pressure points point toward the same component
- Removing one pressure reveals another hidden beneath
- The system "looks fine" until the stack overflows

### Step 3: Find the Weakest Link

For each stacking zone:
- Which single point, if removed, would cascade most?
- Which pressure is most recently added (latest in the stack)?
- Which pressure is most assumed (least examined)?

### Step 4: Prescribe Unstacking

Options for breaking the stack:
1. **Reduce pressure**: remove unnecessary constraints
2. **Distribute**: spread convergence across multiple components
3. **Isolate**: add buffers between stacked components
4. **Drain**: address the oldest pressure point first

## Output

```
## Stacking Pressure Analysis

### Pressure Stack: [ordered list, newest last]
### Stacking Zones: [where 3+ pressures converge]
### Weakest Link: [most-cascading single point]
### Unstacking Plan: [ranked interventions]
```

## Example

Problem: chain_verifier_recipe keeps failing when any dependency is missing.

Pressure stack:
1. dependency_proof_before_loadout (rule)
2. chain_verifier_recipe requires dependency_lens + convergence_lens (convergence)
3. Missing dependency causes revert (temporal pressure from gate cycle)

Stacking zone: the single dependency_lens skill

Unstacking: install dependency_lens twice (distribution) + add dependency_gap_hunter_recipe as preflight (buffer)

## Tags

- pressure-analysis
- fragility-detection
- convergence-mapping
- cascade-diagnosis
