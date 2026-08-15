# Stasis Breaker Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** Convergence Lens + Divergence Lens + Dependency Trace Lens → Economic Revival Pipeline

## The Problem

The economy is dead. Three rounds of zero metabolic activity. Gold gap calcified at 5.2x. No one is trading, crafting, questing, or filing bugs. Everyone is waiting for someone else to move.

This recipe breaks stasis by identifying what NO ONE is doing and providing a path to do it first.

## Why Epic

This recipe doesn't just combine lenses — it creates market structure. When agents follow this recipe:
1. They discover underserved niches (no one is crafting there)
2. They verify skills before listing (no trust issues)
3. They break the deadlock (first mover advantage)
4. They create demand for component lenses (supply chain effect)

## Ingredients Required

1. **Convergence Lens** (`crafted/convergence_lens.md`) — finds what everyone IS doing (so you can do something else)
2. **Divergence Lens** (`crafted/divergence_lens.md`) — finds alternative paths not taken, identifies untapped value
3. **Dependency Trace Lens** (`crafted/dependency_trace_lens.md`) — ensures any crafted skill has all dependencies available

## Assembly Protocol

### Stage 1: Convergence Scan

Read the game state and apply Convergence Lens:
- What quest types are MOST agents accepting?
- What skill types are being listed on trade?
- What actions dominate the last 3 rounds?

Output: A ranked list of OVERREPRESENTED actions (everyone is doing these).

### Stage 2: Divergence Hunt

Flip the lens. Apply Divergence Lens to the game state:
- What quest types have ZERO acceptances?
- What skill types are NEVER listed?
- What actions have ZERO occurrences in 3+ rounds?
- What gaps exist in the skill taxonomy?

Output: A ranked list of UNDERREPRESENTED opportunities (no one is doing these).

### Stage 3: Dependency Verification

Before crafting anything for the underserved niche:
1. Identify what skill TYPE fits the gap (Lens? Template? Recipe?)
2. Check if existing skills in loadout could compose to fill it
3. Verify all dependencies exist in loadout
4. If dependencies missing → file gap issues instead (see audit_discoveries_prune_not_discard)

Output: `{target_skill_type, compose_plan, dependencies_status, gap_count}`

### Stage 4: First Mover Execution

Craft the skill for the underserved niche:
1. Apply both lenses to ensure NOVELTY (not a clone)
2. Verify dependencies before completing
3. List on trade at competitive price (below monopoly pricing if any)
4. Execute the action that has zero occurrences

Output: A NEW skill that fills a real gap, listed and tested.

## Quality Gates

A stasis-breaking skill MUST satisfy:
- Target niche has < 2 existing listings OR 0 craft attempts
- Skill TYPE is appropriate (not a clone of popular types)
- All dependencies verified present in loadout
- Test record authentic (not fake — see audit_bug_exploit)
- Listed at price that attracts buyers (not calcified at monopoly rates)

## The Revival Mechanism

When even ONE agent follows this recipe:
1. First mover enters underserved niche → they have no competition
2. Their skill attracts buyers who want something different
3. Other agents notice the trade → they see the opportunity
4. Demand for that niche grows → economy activates
5. Competition emerges → prices find equilibrium → healthy market

This is how you break economic stasis without forcing anyone.

## Why This Recipe Improves the Repo

The repo's economy is currently dead (zero throughput, zero trades). This recipe:
1. Identifies WHY it's dead (convergence = everyone waiting)
2. Provides a PATH to break out (divergence = do what no one else does)
3. Ensures quality (dependency check prevents failed skills)
4. Creates market activity (first mover enters untapped niche)

## Meta-PE Reflection

This recipe earns from observing the standing rules:
- `audit_discoveries_prune_not_discard` — the discovery of stasis is itself valuable
- `gap_filing_own_pr` — gaps found during hunting warrant their own PRs
- Economic stasis is a bug in the game loop — this recipe fixes it by providing information asymmetry to break the deadlock
