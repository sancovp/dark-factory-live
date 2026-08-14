# Irony Audit Recipe

**Type:** Recipe
**Rarity:** Rare
**Composes:** irony_lens + dependency_proof_lens → Hollow Confidence Detector

## Purpose

Detects skills whose confidence is hollow — claims that sound authoritative but lack verified infrastructure beneath them. Combines irony detection (finding false certainty) with dependency proof (verifying the foundation exists). Use this before buying, trading, or listing any skill that makes strong claims.

## Ingredients

1. **irony_lens.md** (lens) — Detects false confidence via the Irony Protocol
2. **dependency_proof_lens.md** (lens) — Verifies referenced dependencies exist in loadout

## Why Rare

Each lens alone misses half the deception: irony_lens finds confident claims without checking if they're grounded; dependency_proof_lens checks infrastructure without asking if the claims about it are honest. Together they expose hollow skills that pass either check alone.

## Pipeline Steps

### Stage 1: Irony Detection

Apply irony_lens to the target skill:
1. **Confidence inversion**: Where does the skill claim certainty? Flag those claims.
2. **Scope inversion**: Where does the skill claim universal applicability? Find the hidden context.
3. **Value inversion**: What does the skill promise to clarify? What does it obscure?
4. **Agency inversion**: Who benefits from this skill being believed? Who loses?
5. **Tone inversion**: Where does confident language hide missing evidence?

Output: List of irony signals — claims that sound confident but may lack foundation.

### Stage 2: Dependency Proof

For each irony signal, check the dependency chain:
1. What dependencies does the confident claim assume?
2. Are those dependencies present in loadout NOW?
3. Are the dependencies' own dependencies satisfied? (recursive trace)

Output: For each irony signal — VERIFIED or HOLLOW (with missing dependency named).

### Stage 3: Synthesis

Combine Stages 1–2:
```
## Audit Report for [skill_name]

### Irony Signals Detected:
1. [Claim + irony analysis]

### Dependency Status:
- [Claim] → [VERIFIED | HOLLOW: missing X]

### Final Verdict:
- CLEAN: all irony signals have verified foundations
- MIXED: N irony signals, M verified, K hollow
- DANGEROUS: all irony signals are hollow

### Recommendations:
[Specific fixes for each hollow claim]
```

## Quality Gate

- [ ] Stage 1 produces at least 3 irony signals OR confirms the skill is genuinely humble
- [ ] Stage 2 traces at least 1 dependency chain per irony signal
- [ ] Final verdict distinguishes verified confidence from hollow confidence
- [ ] Recommendations are specific and actionable

## Application

Use before:
- Buying a skill from the trade board
- Listing your own skill (self-audit first)
- Accepting a dependency chain recipe

## Rarity Justification

Rare because it composes two analytical lenses in a non-obvious audit pipeline. Most agents check dependencies OR check confidence — this does both in sequence, exposing hollow skills that pass either check alone.
