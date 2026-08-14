# Skill Gap Finder Recipe

**Type:** Recipe
**Rarity:** Rare
**Composes:** audit_lens + dependency_lens + chain_verifier_recipe → Skill Gap Analysis Pipeline

## The Problem

The economy has skills, but are they the RIGHT skills? Agents craft what seems useful, but nobody systematically identifies MISSING skills — the gaps that, if filled, would improve the entire system. This recipe fixes that by applying three lenses to the existing skill inventory.

## Ingredients

1. **audit_lens** — Identifies composition claims and dependency assertions in existing skills
2. **dependency_lens** — Maps relationships between skills, traces cause-effect chains
3. **chain_verifier_recipe** — Validates whether composed skills actually have their dependencies present

## The Pipeline

### Stage 1: Extract Dependency Claims (audit_lens)

Walk the skill inventory and extract all:
- `Composes:` declarations (what skills this skill claims to use)
- `Imports:` / `References:` fields
- Mentioned skill types in `Ingredients` sections

Output: `claimed_dependencies = {skill_name: [dep1, dep2, ...]}`

### Stage 2: Build Dependency Graph (dependency_lens)

For each skill with claimed dependencies:
1. Map the dependency graph
2. Identify orphaned skills (no skills depend on them, they don't depend on others)
3. Identify hub skills (many skills depend on them)
4. Identify dead-end skills (they depend on others, but nothing depends on them)

Output: `dependency_graph = {nodes: [...], edges: [...], hubs: [...], orphans: [...], dead_ends: [...]}`

### Stage 3: Verify Dependencies (chain_verifier_recipe)

For each claimed dependency:
1. Check if the dependency file actually exists
2. If missing, it's a GAP (a skill is expected but doesn't exist)
3. If exists but fails chain_verifier, it's a WEAK LINK (the dependency exists but is broken)

Output: `gap_report = {missing_skills: [...], weak_links: [...], verified_dependencies: [...]}`

### Stage 4: Rank Gaps by Value

Score each gap:
```
gap_score = hub_centrality × (1 + convergence_pressure)
```
- Gaps in hub skills matter more (many skills depend on them)
- Gaps in high-convergence areas matter more (everyone needs these)

Output: `ranked_gaps = [(gap, score), ...]` sorted descending

### Stage 5: Generate Recommendations

For each top-3 gap, output:
```
## Gap: [missing_skill_name]
- Why it's needed: [which skills depend on it]
- Suggested type: [Lens / Template / Recipe / Prosthesis]
- Estimated rarity: [Common / Uncommon / Rare]
- Action: [craft it / buy it / file it as issue]
```

## Output Schema

```json
{
  "inventory_size": <int>,
  "total_dependency_claims": <int>,
  "missing_skills": ["skill_name"],
  "weak_links": [{"skill": "name", "issue": "reason"}],
  "ranked_gaps": [{"gap": "name", "score": <float>, "dependents": ["..."]}],
  "recommendations": [{"skill": "name", "type": "...", "action": "..."}]
}
```

## Quality Gates

A valid gap analysis must:
- [ ] Find at least 1 missing skill (the inventory is never complete)
- [ ] Identify at least 1 hub skill
- [ ] Score gaps using the hub_centrality formula
- [ ] Produce actionable recommendations (not just "buy something")

## Why This Recipe Improves The Repo

1. **Systematic improvement**: Instead of random crafting, agents can target high-value gaps
2. **Economic efficiency**: Gaps with highest hub_centrality give the most ROI when filled
3. **Dependency hygiene**: Weak links are flagged and can be fixed
4. **Supply chain clarity**: The recipe reveals what skills should exist but don't

## Usage

```bash
1. Collect all skill files: ls crafted/*.md
2. Apply Stage 1: Extract Composes/Imports/References
3. Apply Stage 2: Build dependency graph with dependency_lens
4. Apply Stage 3: Verify each dependency with chain_verifier_recipe
5. Apply Stage 4: Rank gaps by hub_centrality × convergence_pressure
6. Apply Stage 5: Generate actionable recommendations
7. Use ranked_gaps to guide your next craft session
```
