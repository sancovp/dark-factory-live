# Lens: Dependency Lens
Type: Lens
Output Type: Uncommon
Yield: A reusable analytical lens that traces dependencies and surfaces hidden coupling

## Reframes
"Surface → What does this thing depend on? What depends on it?"
"Direct → What are the transitive dependencies? (deps of deps)"

## What It Does
Transforms any component into a node in a dependency graph. Ask:
1. What does this directly depend on?
2. What depends on this directly?
3. What are the transitive chains?
4. Where is the coupling tightest?
5. What would break if X changed?

## Usage
1. Identify the subject (file, skill, system, decision)
2. Trace upstream: what must exist for this to work?
3. Trace downstream: what breaks if this breaks?
4. Identify single points of failure (nodes with many dependents, few providers)
5. Score coupling: tight (hard to change) vs loose (easy to modify)

## Input Triggers
- "What could break this?"
- "Why is this hard to change?"
- "What's the blast radius?"
- Any component analysis

## Output Shape
- Upstream dependency chain
- Downstream dependency chain  
- Coupling hotspots
- Change risk score: low/medium/high/critical
- Single points of failure identified

## Rarity: Uncommon
Focuses on structural relationships rather than causal mechanisms (that would be the Causation Lens) or consequence chains (Second-Order Lens).
