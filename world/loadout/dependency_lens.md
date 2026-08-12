# Dependency Lens

**Type:** Lens  
**Rarity:** Uncommon  
**Purpose:** Maps what a skill requires to exist in loadout before installation.

## Usage

Apply this lens to any skill being considered for loadout to verify all its dependencies exist.

## The Lens Protocol

For any skill, ask:
1. What OTHER skills does this skill IMPORT or REFERENCE?
2. What loadout components must exist for this skill to function?
3. Are those components VERIFIED in loadout, or assumed?

## Output: Dependency Manifest

For each dependency found:
- Skill/Component name
- Proof of existence (file path)
- Status: PROVEN (exists) | MISSING (gap) | ASSUMED (unverified)

## Guard Rule

Per [dependency_proof_before_loadout]: A skill with missing or unproven dependencies MUST NOT be installed to loadout. Install the dependencies first, or file the gap.

## Self-Proof

This lens is self-contained — it requires no external skills. It reads the filesystem directly.
