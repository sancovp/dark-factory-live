# Dependency Lens

**Type:** Lens  
**Rarity:** Rare  
**Purpose:** Reframes how to look at a problem by tracing dependencies backward

## The Problem

When examining a skill or component, most agents ask "what does it do?" — but the real question is "what does it REQUIRE?" A component's true risk profile lives in its dependencies, not its surface API.

## The Lens: Trace Dependencies Backward

Instead of asking "what does this skill do?", ask:

### Dependency Questions

1. **What does this skill IMPORT?** (explicit dependencies)
   - Python: `import X`, `from X import Y`
   - Skills: references to other skills by name
   - Files: absolute/relative paths

2. **What does this skill ASSUME?** (implicit dependencies)
   - Environment variables it expects
   - Tools that must be available
   - State it requires to exist
   - Permissions/privileges needed

3. **What would BREAK if a dep is missing?** (failure modes)
   - ImportError → hard fail
   - Missing tool → graceful degradation or silent fail?
   - Bad state → garbage output or crash?

4. **What does this skill ENCOURAGE others to depend on?** (reverse deps)
   - Does it export utilities others will import?
   - Does it define patterns others will copy?
   - Is it a "hub" skill with many dependents?

## The Reframe

**Before (surface view):**
```
Skill X → does Y
```

**After (dependency lens):**
```
Skill X → requires [A, B, C] → does Y → enables [D, E, F]
```

## Usage

Apply this lens when:
- Evaluating a skill for loadout installation
- Auditing a recipe's dependency chain
- Debugging a failing pipeline
- Assessing a skill's portability
- Identifying single points of failure

## Example

**Surface view:** "The test_skill runs skills through Claude"

**Dependency lens view:**
- **Imports:** None (calls external `claude` binary)
- **Assumes:** `claude` binary in PATH, markdown file readable
- **Fails if:** Claude not installed → error message
- **Enables:** Loadout guards, recipe chains, skill verification

## Quality Checklist

When using this lens, document:
- [ ] All explicit imports listed
- [ ] All implicit assumptions noted
- [ ] Failure mode if each dep missing
- [ ] Reverse dependencies identified
- [ ] Overall dependency risk: LOW/MEDIUM/HIGH
