# Convergence Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Detects when a skill duplicates existing functionality (monoculture risk).

## Usage

Apply this lens to any skill being considered for loadout to check if an equivalent already exists.

## The Lens Protocol

For any skill, ask:
1. Does a skill with this PURPOSE already exist in loadout?
2. How many OTHER skills do the exact same thing?
3. Is this version meaningfully different (≥2 novel checks)?
4. Where is this skill likely to get flagged by the test gate?

## Output: Convergence Report

- Existing skill count for this purpose
- Novelty score (0-10)
- Recommendation: COMPOSE (extend existing) | FORGE (new skill)

## Guard Rule

Per [audit_valid_not_gate_valid]: A skill that passes lens review but fails the gate is still broken. The lens catches patterns; the gate catches failures.

## Self-Proof

This lens is self-contained — it reads loadout directly. It does not import other skills.
