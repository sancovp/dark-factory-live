# Loadout Dependency Chain Pipeline Recipe

**Type:** Recipe
**Rarity:** Epic
**Composes:** dependency_lens.md + chain_verifier_recipe.md → End-to-End Loadout Dependency Verification Pipeline

## The Problem

Skills can reference other skills, but do those referenced skills actually exist in the loadout? A skill that imports a missing component is a broken chain waiting to collapse. This recipe combines two lenses into a single verification pipeline that checks both surface claims AND hidden dependency reality.

## Ingredients

1. **Dependency Lens** — Finds what other skills/components the target requires
2. **Chain Verifier Recipe** — Verifies that composition chains actually connect

## The Pipeline Protocol

### Stage 1: Dependency Discovery (via Dependency Lens)
```
1. Parse target skill for import/reference statements
2. Extract all referenced component names
3. Map each reference to its source file path
4. Output: {references: [{name, path, verified}], ...}
```

### Stage 2: Chain Verification (via Chain Verifier Recipe)
```
1. For each verified reference, check if source file exists
2. For each existing source, apply Divergence Lens analysis
3. For each existing source, apply Convergence Lens analysis
4. Synthesize: Are all chains unbroken?
```

### Stage 3: Loadout Safety Verdict
- **All Chains Verified**: Safe for loadout admission
- **Missing References**: NOT safe — list missing components
- **Broken Chains**: NOT safe — composition would fail at gate

## Output Format

```json
{
  "skill": "<target_skill>",
  "references_found": N,
  "references_verified": N,
  "missing_dependencies": [],
  "chain_integrity": "PASS|FAIL",
  "loadout_safe": true|false,
  "recommendations": ["fix missing X", "verify chain Y"]
}
```

## Why This Recipe Works

By combining Dependency Lens (finds references) with Chain Verifier (validates chains):
1. Catches missing dependency bugs BEFORE the gate
2. Prevents broken composition chains from entering loadout
3. Creates a verifiable audit trail for dependency proof

## Example Usage

Target: `chain_verifier_recipe.md`
- References found: [dependency_lens.md, divergence_lens.md, convergence_lens.md]
- References verified: 3/3
- Chain integrity: PASS
- Loadout safe: true
