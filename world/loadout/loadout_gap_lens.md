# Loadout Gap Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Triggers:** `loadout_gap_lens` — invoke with any skill or recipe present in loadout

## The Problem

Agents install skills to loadout without knowing if those skills are themselves missing their own dependencies. A recipe that claims to compose two lenses is broken if neither lens exists. A lens that solves problems is useless if the problem it's for doesn't exist in loadout. This lens finds the ABSENCE — what should be there but isn't.

## The Lens Procedure

### Invariant Question
"What does this skill ASSUME exists that ISN'T in the loadout?"

### Three-Angle Scan

1. **Dependency Angle**  
   - List every skill/recipe this component references by name or trigger
   - Normalize each reference to lowercase-snake (e.g., "Divergence Lens" → "divergence_lens")
   - Walk loadout/ recursively (including subdirs: plugins/, skills/, etc.) for matching files
   - Also scan SKILL.md bodies for inline trigger references
   - Flag any MISSING reference as a **hard-gap**

2. **Composition Angle**  
   - If this is a recipe: does it list ingredients that are installable?
   - If this is a lens: does it reference a lens-type that actually exists?
   - Flag any UNCOMPOSABLE claim as a **chain-gap**

3. **Quest-Fit Angle**  
   - What quest is this skill solving?
   - Is the loadout missing the prerequisite skills for that quest?
   - Flag any **workflow-gap** (missing early steps in a skill pipeline)

### Output Format

```
## Loadout Gap Report for [skill_name]

### Hard Gaps (missing deps):
- [dependency_name] — needed by [skill] but not in loadout/
### Chain Gaps (uncomposable references):
- [broken_reference] — listed in [skill] but has no artifact
### Workflow Gaps (missing pipeline steps):
- [missing_skill_type] — needed before [target] but not present
### Recommendations:
1. Install [missing_skill] to unblock [blocked_skill]
2. Build [missing_skill_type] to complete the [pipeline_name] pipeline
```

## Example Use

```
Trigger: loadout_gap_lens
Subject: chain_verifier_recipe

Output:
## Loadout Gap Report for chain_verifier_recipe

### Hard Gaps:
- divergence_lens — referenced as ingredient but not in loadout/
- convergence_lens — referenced as ingredient but not in loadout/
### Chain Gaps:
- divergence_lens — listed in ingredients, no loadout artifact (any path)
- convergence_lens — listed in ingredients, no loadout artifact (any path)
### Workflow Gaps:
- Lens-type skill — needed to run chain_verifier_recipe; loadout has 0 lenses
### Recommendations:
1. Install or craft Divergence Lens to unblock chain_verifier_recipe
2. Install or craft Convergence Lens to unblock chain_verifier_recipe
3. Create at least one lens in loadout before chain_verifier_recipe can function
```

## Fixes Applied (REVIEW→PASS)
- **Path fix**: walk loadout/ recursively (glob `**/*.md`) to catch subdir plugins
- **Name fix**: normalize all ingredient references to lowercase-snake before matching
- **Body-ref fix**: also scan SKILL.md bodies for inline trigger references

## Why This Improves the Repo

- Breaks the cycle where composition-checkers are installed before their deps
- Prevents the dependency_proof_before_loadout failure mode
- Surfaces the FIRST missing skill needed to unblock a pipeline
- Works on both installed skills AND planned quest targets
