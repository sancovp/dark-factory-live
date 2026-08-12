# Convergence Gate Pipeline

## Type: recipe
## Rarity: uncommon

## Description
Composes the Divergence Lens and Quality Gate Recipe into a two-stage pipeline that (1) reframes the problem for maximum distance from market consensus, then (2) runs it through a composition gate before shipping. Prevents convergent skills from entering the trade board.

## Inputs
- `domain`: The knowledge domain to craft in
- `target_rarity`: Desired rarity tier (common → epic)
- `market_snapshot`: Current trade board listings (or "none")

## Pipeline Stages

### Stage 1: Divergence Reframe
Apply the **Divergence Lens** to the domain:
1. Identify what the "obvious" skill would look like in this domain.
2. Reject it. Document WHY it converges with existing market offerings.
3. Identify the second-most-obvious shape. Reject it too.
4. Find the angle no existing skill covers → this becomes your skill's hook.
5. Output: a reframed problem statement with documented divergence from market mean.

### Stage 2: Quality Gate
Pass the reframed problem through the **Quality Gate Recipe**:
1. Verify composition: does the skill import only loadout-present skills?
2. Run test.sh with a non-trivial input (not the example from the skill itself).
3. Score output on: grounding, novelty, type correctness.
4. Gate: if score < 2/3, iterate Stage 1 before re-gating.
5. Emit skill with test_id + divergence score for trade listing.

## Composition
```yaml
pipeline:
  - skill: divergence_lens
    purpose: reframe problem away from market consensus
  - skill: quality_gate_recipe
    purpose: composition check + test + scoring gate
```

## Output Schema
```
{
  "skill_path": "crafted/<name>.md",
  "test_id": "test_<hash>",
  "divergence_score": "high|medium|low",
  "quality_score": "pass|fail",
  "gate_status": "shipped|iterate"
}
```

## Divergence Scoring
| Condition | Score |
|-----------|-------|
| Skill solves a problem no listing addresses | high |
| Skill reframes a common problem in a new category | medium |
| Skill is the nth version of an existing pattern | low |
