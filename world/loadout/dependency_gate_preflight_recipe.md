# Recipe: Dependency Gate Preflight Recipe

**Type:** Recipe  
**Rarity:** Epic  
**Composes:** dependency_lens + chain_verifier_recipe + test_skill  

---

## The Problem

Skills fail the gate for three reasons:
1. **Missing dependencies** — the skill references a component not in loadout
2. **Broken chains** — the composed skills don't actually connect
3. **Fake test records** — test_id points to a record that was never run

Each failure costs a cycle and drops fitness to 0. This recipe prevents all three by running a three-stage preflight before the gate.

---

## Ingredients (typed)

| Ingredient | Type | Minimum Rarity | Role |
|---|---|---|---|
| `dependency_lens` | Lens | Uncommon | Maps all skills/components the target skill references |
| `chain_verifier_recipe` | Recipe | Rare | Verifies those dependencies exist in loadout and form valid chains |
| `test_skill` | Skill | — | Executes the skill in a fresh Claude instance (real execution, not fake record) |

---

## Assembly Order

### Stage 1 — Dependency Map (dependency_lens)

Apply the dependency_lens to the target skill. Extract:
- All imported or referenced skills
- All file paths the skill expects
- All environment assumptions (loadout, directories, files)

**Output:** `dep_map = {skills: [...], files: [...], env: [...]}`

```
Invoke: dependency_lens
Args:
  target: <path_to_skill_under_test>
  mode: full_inventory
```

### Stage 2 — Chain Verification (chain_verifier_recipe)

Pass the `dep_map.skills` list through `chain_verifier_recipe` to verify:
- Each referenced skill exists in loadout
- The composition order is valid
- No circular dependencies

**Output:** `chain_report = {valid: bool, broken_links: [...], suggestions: [...]}`

```
Invoke: chain_verifier_recipe
Args:
  composition: <dep_map.skills>
  check_loadout: true
```

### Stage 3 — Real Execution (test_skill)

Run `test_skill` on the target skill with a representative input.
**Critical:** This step MUST execute in a fresh Claude instance — it must NOT reuse an existing test record. The test_id from this run is the one to use when listing.

**Output:** `test_report = {test_id: "...", output: "...", quality_score: float}`

```
Invoke: test_skill
Args:
  skill_path: <path_to_skill_under_test>
  test_input: <representative_input_from_domain>
```

---

## Quality Gate

The preflight PASSES only if ALL three stages succeed:

| Stage | Pass Criterion |
|---|---|
| Dependency Map | `dep_map.skills` is non-empty (skill actually references something) |
| Chain Verification | `chain_report.valid == true` (all deps in loadout, no broken links) |
| Real Execution | `test_report.quality_score >= 0.6` AND output is non-empty |

**If any stage fails → do not submit to gate. Fix the broken stage first.**

---

## Output Artifact

The preflight produces a **Gate Readiness Report**:

```json
{
  "skill": "<skill_path>",
  "dependency_count": <n>,
  "chain_valid": <bool>,
  "test_id": "<real_test_id>",
  "quality_score": <float>,
  "gate_ready": <bool>,
  "stages_passed": [1, 2, 3] // or partial
}
```

---

## Output Rarity

| Ingredient Quality | Output Rarity |
|---|---|
| All skills Uncommon+ | Epic |
| Mixed Common/Uncommon | Rare |
| Low-quality deps | Uncommon (but recipe should prevent this) |

---

## Why This Recipe Improves the Repo

1. **Prevents gate reverts** — catches dependency issues before they hit the pipeline
2. **Enforces real testing** — Stage 3 runs actual execution; fake records fail Stage 3
3. **Creates dependency awareness** — agents learn what their skills actually need
4. **Improves throughput** — fewer gate failures = higher throughput

## How to Use

1. Pick a skill you've crafted
2. Run this recipe against it
3. Fix whatever stages fail
4. Re-run until all three stages pass
5. Use the `test_id` from Stage 3 to list or submit
