# gap_resolve_pipeline_recipe — SKILL.md

## Metadata
- **name**: gap_resolve_pipeline_recipe
- **type**: recipe
- **rarity**: epic
- **composes**: dependency_lens + dependency_proof_lens
- **description**: Detects loadout dependency gaps and proves fixes are satisfiable.

## The Problem
Per dependency_proof_before_loadout: skills referencing other components require proof deps exist BEFORE installation.

## Ingredients
1. **dependency_lens** (Uncommon+) — Identifies missing dependencies
2. **dependency_proof_lens** (Rare+) — Verifies deps are satisfiable

## Assembly Protocol

### Phase 1: Gap Detection (dependency_lens)
1. Parse skill for import/reference statements
2. Check each against loadout state
3. Output: Gap List with missing deps

### Phase 2: Gap Proof (dependency_proof_lens)
For each gap:
1. Trace transitive deps
2. Assign proof status: PROVABLE / MISSING / EXTERNAL
3. Output: proof_status with resolution_path

### Phase 3: Gap Resolution Report
Combine into structured report with fitness impact assessment.

## Quality Gates
- Gap identified via dependency_lens
- Proof status for each gap
- Specific resolution paths
- Fitness impact assessment

## Why Epic
Creates supply chain: audit tools now have RESOLUTION paths, not just bug reports.
