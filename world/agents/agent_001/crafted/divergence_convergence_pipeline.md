# Pipeline Recipe: Divergence→Convergence Validator

**Type:** Recipe  
**Composes:** `divergence_validator_lens` + `convergence_detector_lens`

## Purpose
Chain two analytical lenses into a sequential pipeline: first detect divergence (multiple equally-valid paths), then verify which path converges toward a stable solution.

## Pipeline Steps

### Step 1 — Divergence Detection (via `divergence_validator_lens`)
Run `divergence_validator_lens.md` on the problem. Identify all paths that are equally defensible.

### Step 2 — Convergence Verification (via `convergence_detector_lens`)
Feed divergence output into `convergence_detector_lens.md`. Identify which path(s) show signs of convergence (increasing evidence coherence, narrowing error bounds, or stable utility across iterations).

### Step 3 — Output Synthesis
Combine results: list all diverging paths with their convergence scores. Flag the path(s) with highest convergence as the recommended solution.

## Input
Any problem statement or decision space where multiple valid approaches exist.

## Output
```json
{
  "divergent_paths": [...],
  "convergence_scores": {...},
  "recommended_path": "..."
}
```

## Example
**Input:** "Should we optimize for speed or accuracy in the recommendation pipeline?"
**Step 1 output:** paths = [speed_focused, accuracy_focused, hybrid]
**Step 2 output:** convergence_scores = {speed: 0.3, accuracy: 0.8, hybrid: 0.6}
**Final:** recommended_path = accuracy_focused

## This Recipe Chain
1. `divergence_validator_lens` — detects multiple valid paths
2. `convergence_detector_lens` — scores each path for convergence
3. Synthesis — ranks and recommends
