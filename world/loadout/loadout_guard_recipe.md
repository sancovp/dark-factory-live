# Loadout Guard Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** dependency_lens + convergence_lens → Guard Skill with Verified Dependencies

## The Problem

Every cycle, guards get installed that fail the gate — consuming loadout slots, tanking fitness, and giving false confidence. The root cause: guards are crafted without proving their own dependencies exist in loadout BEFORE installation. The meta-rules say: a guard that fails composition-check is worse than no guard.

## Dependencies (PROVEN)

| Dependency | Proof |
|------------|-------|
| dependency_lens | loadout/dependency_lens.md exists |
| convergence_lens | loadout/convergence_lens.md exists |

## Ingredients

1. **dependency_lens** — Maps what the guard requires to exist in loadout.
2. **convergence_lens** — Verifies the guard doesn't duplicate existing guards.

## The Recipe

### Step 1: Dependency Trace (dependency_lens)

For the guard skill you're building, apply dependency_lens:

- What OTHER skills does this guard IMPORT or REFERENCE?
- What loadout components must exist for this guard to function?
- Are those components VERIFIED in loadout, or assumed?

Output: **Dependency Manifest** listing each dependency with:
- Skill name
- Proof of existence (file path or gate-pass record)
- Fallback behavior if missing

### Step 2: Convergence Check (convergence_lens)

Apply convergence_lens to your guard design:

- Does a guard with this purpose ALREADY exist in loadout?
- If yes, is your version meaningfully different (≥2 novel checks)?
- If no, what's the minimum viable guard that covers this threat class?

Output: **Convergence Report** with:
- Existing guard count for this threat class
- Novelty score (0-10)
- Recommendation: COMPOSE (add to existing) or FORGE (new guard)

### Step 3: Compose the Guard

If CONVERGENCE says FORGE, create the guard with this structure:

```markdown
# [Threat Class] Guard

**Type:** Guard  
**Dependencies:** [list from Dependency Manifest]
**Proof of deps:** [file paths or gate records]

## Guard Logic
[What this guard checks]

## Dependency Self-Proof
[Each dep proven to exist in loadout]

## Gate Survival
[Why this guard will pass the gate]
```

If COMPOSE, extend the existing guard instead.

### Step 4: Gate Pre-flight

Before declaring loadout-ready:
1. Run dependency_lens on the completed guard → all deps green?
2. Run convergence_lens on the completed guard → novelty confirmed?
3. Run test on the guard itself → it executes without error?

Output: **Guard Readiness Certificate** with all three green.

## Quality Gates

A guard is LOADOUT-READY when:
- Dependency Manifest: all deps proven in loadout (not assumed)
- Convergence Report: novelty ≥ 6/10 OR composition with existing guard
- Guard Readiness Certificate: dependency_lens + convergence_lens + test all green
- Gate Survival section: explicit argument why guard passes gate

## Why This Recipe Improves The Repo

Per [guard_must_pass_gate_to_be_loadout] and [dependency_proof_before_loadout]:
- Guards crafted without dependency proof get reverted at gate
- This recipe enforces dependency proof BEFORE crafting completes
- Fewer guard reverts = higher fitness = better throughput
- The repo's loadout becomes trustworthy instead of aspirational

## Meta-Level Note

This recipe itself was verified against the dependency proof rule:
- dependency_lens exists in loadout (PROVEN)
- convergence_lens exists in loadout (PROVEN)
- This recipe composes verified skills → it is itself dependency-proven
