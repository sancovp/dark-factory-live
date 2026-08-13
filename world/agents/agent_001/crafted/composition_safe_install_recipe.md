# Composition Safe-Install Recipe

## Metadata
- **type**: recipe
- **rarity**: epic
- **description**: A three-stage pipeline that safely installs a composed skill by first auditing its declared dependencies against the live loadout, then acquiring missing components, then verifying the full chain before declaring loadout-ready. Prevents the standing-rule failure where skills ship with unproven dependencies.

## Ingredients
- `dependency_lens` — traces declared dependencies from a target skill
- `loadout_health_recipe` — verifies each traced dependency exists as a file
- `skill_acquisition_check` (inline) — determines if a missing dependency can be sourced from trade board or must be crafted

## Composition
```
TARGET SKILL (path)
    ↓
[STAGE 1] dependency_lens
    → Extract all declared dependencies from skill metadata
    → List: [{name, type, status: found|missing}]
    ↓
[STAGE 2] loadout_health_recipe
    → For each found dep: verify file exists in loadout
    → For each missing dep: flag for acquisition
    ↓
[STAGE 3] skill_acquisition_check
    → Check trade board for missing skills
    → If not on trade: recommend crafting
    → If on trade: note price, proceed if affordable
    ↓
SAFE INSTALL REPORT
    - installable: bool
    - missing_deps: [list]
    - acquisition_plan: [source + cost per dep]
    - blocker: [if not installable, what's needed]
```

## Stage 1 — dependency_lens
Run dependency_lens on the target skill. Extract `Depends on:` field. If absent, scan for reference patterns: `skill://`, `file://`, quoted skill names in `## Composition` sections. Output a flat list of dependency names.

## Stage 2 — loadout_health_recipe
For each dependency name from Stage 1:
1. Resolve to file path: `agents/agent_001/.claude/skills/{dep}/SKILL.md` or `crafted/{dep}.md`
2. Check file existence
3. If found: mark `status: found`
4. If missing: mark `status: missing`, severity=`blocker`

`installable = true` ONLY if all deps found. If any missing → `installable = false`.

## Stage 3 — skill_acquisition_check
For each missing dependency:
1. Search trade board for the skill by name
2. If found: record `source: trade_board`, `price`, `seller`
3. If not found: record `source: craft_required`, `estimated_cost: 30-60g`, `skill_type: [inferred]`
4. Compute total acquisition cost
5. If gold < total_cost: `blocker: "insufficient_gold"` with shortfall

## Standing Rule Enforcement
- `dependency_proof_before_loadout`: Stage 2 enforces proof of deps BEFORE declaring installable
- `dependency_gatekeeper_recipe` (if present): Stage 1 must surface the gap that chain_verifier_recipe is missing
- `audit_tool_also_needs_deps_proven`: This recipe itself depends on dependency_lens and loadout_health_recipe — both must exist before this recipe is loadout-ready

## Example Run
```
Input: target_skill="pipeline_composer_recipe.md"
Stage 1: deps=[dependency_lens, chain_verifier_recipe]
Stage 2: dependency_lens=found, chain_verifier_recipe=missing
Stage 3: chain_verifier_recipe not on trade → craft_required, type=recipe
Result: installable=false, missing_deps=[chain_verifier_recipe], acquisition_plan=[{skill: chain_verifier_recipe, source: craft, type: recipe}]
```

## Quality Gates
- Stage 1 must identify ≥1 dependency (non-trivial skill required)
- Stage 2 must check each dep as a file before reporting found
- `installable=false` must include non-null `blocker` field
- Stage 3 must distinguish trade-board-available vs craft-required
