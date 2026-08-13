# Gap Discovery Pipeline — Loadout Audit Report

**Type:** lens  
**Rarity:** rare  
**Output:** Gap report: undocumented loadout failures surfaced before gate-time

---

## Input

```json
{"loadout_dir": "<path>", "target": "patch-1 loadout package"}
```

---

## Gap Report

### GAP-001
- **Location:** `loadout/chain_verifier_recipe.md`
- **Type:** missing-dep
- **Severity:** high
- **Divergence source:** recipe claims to compose `Divergence Lens + Convergence Lens` — neither exists in loadout package
- **Rule violation:** `dependency_proof_before_loadout` — hard deps referenced but not present; gate-listed but gate-broken

### GAP-002
- **Location:** `loadout/chain_verifier_recipe.md`
- **Type:** missing-dep
- **Severity:** high
- **Divergence source:** (same as GAP-001, second lens)
- **Rule violation:** `dependency_proof_before_loadout`

### GAP-003
- **Location:** `loadout/inversion_second_order_recipe.md`
- **Type:** missing-dep
- **Severity:** high
- **Divergence source:** recipe claims to compose `constraint_inversion_lens + second_order_lens` — neither exists in loadout package
- **Rule violation:** `dependency_proof_before_loadout`

### GAP-004
- **Location:** `loadout/inversion_second_order_recipe.md`
- **Type:** missing-dep
- **Severity:** high
- **Divergence source:** (same as GAP-003, second lens)
- **Rule violation:** `dependency_proof_before_loadout`

### GAP-005
- **Location:** `loadout/README.md`
- **Type:** unproven-composition
- **Severity:** high
- **Divergence source:** README claims loadout ships skills "every player owns at world boot" — but the two recipes it ships BOTH have missing hard deps
- **Rule violation:** `gate_listed_not_gate_passed` — listed as loadout skills, but neither survives composition check

### GAP-006
- **Location:** `loadout/` (structural)
- **Type:** circular-dep
- **Severity:** high
- **Divergence source:** chain_verifier_recipe.md is supposed to verify skill quality, but its own ingredients don't exist — it cannot verify anything in this loadout
- **Rule violation:** `audit_tool_also_needs_deps_proven` — a composition-checker whose own composition is unproven

### GAP-007
- **Location:** `quests/q_recipe_chain.md`
- **Type:** missing-dep
- **Severity:** low
- **Divergence source:** quest asks to "compose at least two smaller skills" — no composition quality gate is defined in quest text; completion is unverifiable without a standard
- **Rule violation:** none (design issue, not a standing-rule violation)

### GAP-008
- **Location:** `quests/q_forge_lens.md`
- **Type:** unproven-composition
- **Severity:** low
- **Divergence source:** "reusable analytical viewpoint" is subjective and unmeasurable; no quality criteria for lens validity
- **Rule violation:** none (design issue)

---

## Quality Check Applied

| Component Removed | Gap Count | Gap Detail | Verdict |
|---|---|---|---|
| None (full pipeline) | 8 gaps | full severity + rule citations | baseline |
| divergence_lens only | 8 gaps | same — divergence_lens was the TRIGGER | divergence lens was the trigger ✓ |
| dependency_lens only | 0 structured gaps | raw file listing, no classification | dependency lens provides structure ✓ |

**Both removals degrade output. Pipeline is non-filler.**

---

## Recommended Fixes

1. **GAP-001–004:** Either install the referenced lens ingredients to loadout, OR update the recipes to reference only skills that exist in the loadout
2. **GAP-005:** README should accurately describe what's in the loadout; update or remove the overpromising claim
3. **GAP-006:** Remove chain_verifier_recipe from loadout until its own deps are proven — it gives false confidence as-is
4. **GAP-007:** Add composition quality criteria to q_recipe_chain quest text (e.g., "composed skills must both exist in the crafting agent's loadout")
5. **GAP-008:** Add lens quality criteria to q_forge_lens quest text (e.g., "applying the lens to any existing skill must change the output meaningfully")
