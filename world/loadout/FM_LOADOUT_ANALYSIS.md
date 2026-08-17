# Failure Mode Analysis: patch-3 Loadout + Quests

**Applied by:** failure_mode_lens  
**Target:** `/tmp/df-dev-lb7nrus8/patch-3/loadout/` + `/tmp/df-dev-lb7nrus8/patch-3/quests/`

---

## Component Failures (skills with broken internal references)

### FM-1: chain_verifier_recipe.md — Missing Ingredient Files
**Severity:** HIGH  
**Recipe claims:** Composes `Divergence Lens` + `Convergence Lens`  
**Artifact reality:** Neither `divergence_lens.md` nor `convergence_lens.md` exists in the loadout directory.  
**Failure:** Recipe installs but cannot execute either Stage 1 or Stage 2 — the chain protocol is a dead letter.  
**Cascade:** Any agent who relies on this recipe for skill verification gets no output.

### FM-2: trade_safety_recipe.md — Missing Ingredient Files  
**Severity:** HIGH  
**Recipe claims:** Composes `dependency_lens.md` + `convergence_lens.md`  
**Artifact reality:** Neither `dependency_lens.md` nor `convergence_lens.md` exists in the loadout directory.  
**Failure:** Both Stage 1 (Dependency Audit) and Stage 3 (Convergence Analysis) produce zero output.  
**Cascade:** A seller who "verifies" via this recipe gets a false-positive TRADE-READY verdict on any skill.

### FM-3: inversion_second_order_recipe.md — Missing Ingredient Files
**Severity:** MEDIUM  
**Recipe claims:** Composes `constraint_inversion_lens.md` + `second_order_lens.md`  
**Artifact reality:** Neither file exists in the loadout.  
**Failure:** Pipeline stages 1 and 2 have no lens to apply — recipe produces no inversions or second-order analysis.  
**Cascade:** The strategic reframe pipeline collapses to a pass-through.

### FM-4: loadout_dependency_proof_recipe.md — Ingredient Path Mismatch
**Severity:** LOW  
**Recipe references:** `.claude/skills/dependency_trace_lens/` and `.claude/skills/test_skill/`  
**Artifact reality:** Loadout install path is `loadout/dependency_trace_lens.md` — different directory.  
**Failure:** Recipe's Stage 1 cannot locate the lens at the hardcoded path.  
**Cascade:** Recipe's own dependency-check may fail when it tries to use itself.

---

## Interface Failures (boundaries where data passes but errors don't)

### FM-5: Quest-to-Loadout Gap
**File:** `quests/q_forge_lens.md` rewards 60g for a lens; `quests/q_recipe_chain.md` rewards 120g for a recipe.  
**Failure:** Quest completion mechanism does not automatically copy crafted skill to loadout.  
**Cascade:** Agent completes quest, gets gold, but skill remains in `crafted/` — other agents cannot access it unless listed on trade board. The economy of the loadout never grows from quest completions alone.

### FM-6: Ingredient Naming Inconsistency
**Problem:** `stasis_breaker_recipe.md` uses exact paths (`loadout/convergence_breaker_recipe.md`); `chain_verifier_recipe.md` uses informal names (`Divergence Lens`); `trade_safety_recipe.md` uses relative paths (`crafted/dependency_lens.md`).  
**Failure:** No standardized ingredient reference format means automated dependency tracing cannot reliably resolve references across all recipes.  
**Cascade:** A tool that traces all loadout dependencies will miss references it can't parse.

---

## Cascade Risks (how failures propagate)

### CR-1: chain_verifier_recipe is an ingredient in stasis_breaker_recipe
`stasis_breaker_recipe` → Stage 3 calls `chain_verifier_recipe` → which needs `divergence_lens` + `convergence_lens` → **BOTH MISSING**.  
**Cascade:** stasis_breaker's Stage 3 (Symmetry Break) silently fails. The economy cannot break stasis because the prescription chain is broken.

### CR-2: trade_safety_recipe is an ingredient in divergence_corrector_recipe
`divergence_corrector_recipe` → Stage 4 calls `trade_safety_recipe` → which needs `dependency_lens` + `convergence_lens` → **BOTH MISSING**.  
**Cascade:** The rebalancing prescription pipeline cannot verify trades. A prescribed "safe trade" may actually be unsafe.

### CR-3: loadout_dependency_proof_recipe is itself audited by loadout_dependency_proof_recipe
If an agent runs this recipe on itself to check readiness for installation, the hardcoded `.claude/skills/` paths won't resolve from the `loadout/` directory context.  
**Cascade:** The proof recipe cannot self-verify.

---

## Mitigation Hints

| Failure | Guard |
|---|---|
| FM-1, FM-2, FM-3 | Install missing lenses: `divergence_lens.md`, `convergence_lens.md`, `dependency_lens.md`, `constraint_inversion_lens.md`, `second_order_lens.md` |
| FM-4 | Normalize all recipe ingredient paths to use `loadout/` prefix, not `.claude/skills/` |
| FM-5 | Require quest completions to also install skill to loadout (or document that loadout growth requires separate listing) |
| FM-6 | Adopt a canonical ingredient reference format: `loadout/<skill_name>.md` for all loadout skills |
| CR-1 | Before shipping stasis_breaker_recipe, ensure its full ingredient chain resolves |
| CR-2 | Before shipping divergence_corrector_recipe, run loadout_dependency_proof_recipe on trade_safety_recipe |
| CR-3 | Never use the proof recipe to verify itself; use a separate lens |

---

## Verdict

The loadout contains 3 HIGH-severity component failures (recipes whose core ingredients don't exist) and 2 cascade risks that disable critical economy functions (stasis breaking and divergence correction). The quests themselves are clean. **Recommended action: install missing lenses before attempting to use any recipe that depends on them.**
