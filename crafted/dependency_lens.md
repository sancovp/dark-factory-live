# Lens: Dependency Topology Lens
Type: Lens
Output Type: Prism (Rare)
Yield: 1 reusable analytical lens for mapping system dependencies and finding hidden coupling

## Reframes
**FROM:** "What does this system/claim depend on?"
**TO:** "What does this system/claim ACTUALLY depend on, and what depends on it?"

**FROM:** "Where are the inputs?"
**TO:** "Where are the HIDDEN inputs — the assumptions, external services, and implicit contracts?"

## How to Apply
1. Identify the DIRECT dependencies (what this explicitly uses/requires)
2. Trace BACKWARDS to find HIDDEN dependencies (inherited assumptions, ambient context)
3. Trace FORWARDS to find DEPENDENTS (what breaks if this breaks)
4. Mark each node as:
   - [EXPLICIT] — stated, visible, manageable
   - [IMPLICIT] — assumed, invisible, dangerous
   - [CRITICAL] — single point of failure if removed
5. The lens fires when you find [IMPLICIT] + [CRITICAL] = hidden coupling

## Example Reframe
- Input: "This API call fetches user data"
- Lens fires: "What fetches the API credentials? What validates the user schema? What handles the case when the auth service is down but the data service is up?"
- Hidden dependencies revealed: auth service, schema registry, partial-failure handlers

## Quality Check
- Without this lens, can you find hidden dependencies? (Must: no → lens is essential)
- Does every CRITICAL node have an explicit management strategy? (Must: yes → lens found a gap)
- Is the dependency graph fully connected? (Must: no → disconnected clusters = unknown unknowns)

## Expected Rarity: Rare
- Novel perspective not covered by causation or risk lenses
- Identifies structural coupling invisible to other analyses
