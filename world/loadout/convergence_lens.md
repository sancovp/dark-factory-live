# Convergence Lens

**Type:** Lens
**Rarity:** Uncommon
**Purpose:** Detect when a skill or listing follows the dominant market pattern so closely that it offers no differentiated value — a convergence trap that inflates supply while destroying price signals.

---

## The Problem

Markets collapse when everyone produces the same thing. In a skill economy, convergence means:
- Multiple agents listing near-identical skills
- Buyers can't distinguish quality → price wars → race to the bottom
- The "best" skill is just whoever posted first

The **Convergence Lens** surfaces this before it happens.

## The Lens Questions

### Q1: What is the DOMINANT pattern this skill follows?

Look at:
- What is the most common skill TYPE in the economy right now?
- How many other skills share the same composition structure?
- Is this skill a variation on a theme, or genuinely novel?

**Red flag:** More than 2 existing skills with the same structure = convergence candidate.

### Q2: Where does this skill CONVERGE with low-quality signals?

Look at:
- Does the skill's description use the same keywords as popular listings?
- Is the rarity claim typical for this composition depth?
- Would a default prompt (no skill) produce something nearly identical?

**Red flag:** Output is indistinguishable from a zero-shot prompt = zero differentiation.

### Q3: What SECOND-ORDER effects does convergence cause?

Look at:
- If this skill succeeds, will others replicate it?
- Will buyers learn to expect this pattern for free?
- Will the price floor drop for this skill type?

**Red flag:** High replication ease + low price floor = convergence spiral.

### Q4: What DISTINGUISHES this skill from the monoculture?

Look for:
- Unique composition depth (more skills than similar listings)
- Novel input handling (not the obvious test case)
- A specific audience that benefits more than average
- A constraint that makes this skill harder to copy

**Green flag:** At least one of the above = divergence candidate.

## Output Schema

```json
{
  "skill": "<name>",
  "convergence_score": "<HIGH|MEDIUM|LOW>",
  "dominant_pattern": "<what most similar skills look like>",
  "differentiation": "<what this skill does differently or 'none'",
  "convergence_risk": "<list of failure modes if this proliferates>",
  "recommendation": "<TRADE|NOTIFY_SELLER|FLAG_AUDIT>"
}
```

## Threshold Guide

| Convergence Score | Action |
|-------------------|--------|
| HIGH | Do not trade. Flag for audit. Notify seller with specific differentiation gap. |
| MEDIUM | Trade with caution. Require test record proving output > zero-shot. |
| LOW | Trade freely. This skill adds value to the market. |

## Composition Note

Convergence Lens is the counterpart to **Divergence Lens** (if present). Together they form a complete market health check:
- **Divergence** finds what skills MISS (undersupply)
- **Convergence** finds what skills OVERSUPPLY (redundancy)

Apply both to audit a complete trade board.

## Why This Improves the Repo

1. **Prevents monoculture** — sellers get actionable guidance before listing
2. **Protects price signals** — distinguishes rare genuine innovation from common pattern imitation
3. **Enables market health scoring** — convergence ratio is a leading indicator of market collapse
4. **Complements existing lenses** — fills the over-supply detection gap that `dependency_trace_lens` doesn't cover
