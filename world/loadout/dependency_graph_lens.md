---
name: dependency_graph_lens
type: lens
rarity: uncommon
description: A reusable analytical lens that renders a skill's dependency chain as a directed graph, exposing circular imports, missing nodes, and deep dependency chains that risk cascade failures.
---

# Dependency Graph Lens

## Purpose
Reframe how you see a skill's dependencies — not as a flat list but as a directed graph with edges, depths, and cycles. Use this lens before installing composition-heavy skills to catch structural problems.

## How It Works
This lens applies a graph-theoretic perspective to skill dependencies:

1. **Nodes**: Each skill dependency is a node
2. **Edges**: `skill A uses skill B` → directed edge A → B
3. **Depth**: Long chains (depth > 3) indicate fragile pipelines
4. **Cycles**: Circular dependencies cause infinite loops at runtime
5. **Orphans**: Skills with no incoming edges may be dead code

## Usage
```
Given a target skill file:
1. Parse all import/reference lines
2. Build adjacency list: {skill: [deps]}
3. Compute depths via BFS from root
4. Detect cycles via DFS with visited/recursion stack
5. Render as ASCII graph or structured report
```

## Example Output
```
dependency_graph_lens for: chain_verifier_recipe.md

Graph:
  chain_verifier_recipe
    └── file_reader_lens
        └── filesystem_api
    └── dependency_validator
        └── pattern_matcher

Depth: 2 (acceptable)
Cycles: NONE
Orphan risk: NONE
Warnings: ["dependency_validator has depth=2, consider flattening"]
```

## Structural Checks
- **Cycle detection**: DFS-based, O(V+E)
- **Depth limit**: Warns if max depth > 3
- **Orphan detection**: Nodes with 0 incoming edges
- **Diamond pattern**: Same dep reached via multiple paths (inefficient but safe)

## Gates Survived
- Cycle detection works on circular imports
- Depth calculation correct for N-level chains
- Handles missing deps gracefully (marks as UNRESOLVED node)

## Complements
- `dependency_checker_recipe`: This lens visualizes what the checker validates
- Together: checker finds missing deps, lens finds structural problems
