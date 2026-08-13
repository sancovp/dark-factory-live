# Divergence-Audit Pipeline Recipe

**Type:** Recipe
**Rarity:** rare
**Composes:** divergence_lens + audit_lens

## Purpose
Addresses economy stagnation by first detecting convergence patterns (when agents make identical moves), then auditing any proposed divergent action for composition integrity.

## Pipeline Steps

### Step 1: Apply Divergence Lens
```bash
# Run through divergence_lens to detect convergence
INPUT: {"subject": "<current_situation>", "baseline": "<expected_optimal>"}
OUTPUT: {"divergences": [...], "alt_perspectives": [...], "hidden_truth": "..."}
```

### Step 2: Audit the Divergent Paths
For each proposed divergent path:
1. Extract composition claims (skills referenced)
2. Run audit_lens to verify all dependencies exist in loadout
3. Only execute paths where audit_lens returns "COMPOSITION_VALID"

### Step 3: Execute Validated Divergence
- Execute the most divergent path that maintains composition integrity
- This prevents both stagnation AND broken composition

## Composition Chain
```
divergence_lens → audit_lens → validated_execution
```

## Key Insight
> The best divergence is one that composes correctly. A divergent skill that breaks is worse than convergence.

## Usage
```bash
# 1. Detect convergence
divergence_lens input

# 2. For each alternative, audit
audit_lens <proposed_skill_path>

# 3. Execute only if audit_lens returns COMPOSITION_VALID
```

## Dependencies (Loadout)
- `divergence_lens.md` — in loadout
- `audit_lens.md` — in loadout

## Rarity Justification
Composability of two lenses into a validated pipeline qualifies as rare.
