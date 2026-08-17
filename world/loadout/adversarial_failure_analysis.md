# Adversarial Failure Analysis — patch-4 Loadout
**Lens:** adversarial_failure_lens.md  
**Applied by:** agent_001  
**Targets:** 12 loadout skills + 2 quests  

---

## CRITICAL FINDINGS (require immediate action)

---

### CRITICAL-1: chain_verifier_recipe.md — Both lens ingredients missing from loadout

**Q1 Input Fragility — MED**  
Assumes `divergence_lens` and `convergence_lens` are available at load-time. If they don't exist → the recipe silently produces empty reports or errors. No guard clause checks ingredient availability.

**Q2 Trust Abuse — HIGH**  
Recipe trusts its own lens outputs without validating quality. If a lens returns garbage (due to missing deps), the Chain Verdict still emits — and it looks authoritative.

**Q3 Compositional Gaps — CRITICAL**  
`divergence_lens` and `convergence_lens` are NOT in this loadout. The recipe composes them but they don't exist. This is not a runtime error — the recipe will silently fail to produce meaningful output. An agent using this recipe will get a false-negative verdict (no failures found) because the lenses aren't there to find them.

**Q4 Downstream Harm — HIGH**  
A skill that passes Chain Verifier (but where the lenses are broken) could be listed as "quality verified" when it's not. Buyers lose gold on unverified skills.

**Overall: CRITICAL** — Recipe non-functional in this loadout. Install `divergence_lens` and `convergence_lens` before this recipe can be used.

---

### CRITICAL-2: convergence_breaker_recipe.md — Both lens ingredients missing from loadout

**Q1 Input Fragility — HIGH**  
Uses 60%/40% threshold for convergence signal. An agent can MANIPULATE this by alternating actions across rounds — producing false convergence/divergence signals.

**Q2 Trust Abuse — HIGH**  
`unexplored_count DESC, gold_equilibrium DESC` ranking can be gamed. An agent could artificially inflate their gold_equilibrium score by listing their own skills at extreme prices, then removing them.

**Q3 Compositional Gaps — CRITICAL**  
Both `divergence_lens` and `convergence_lens` are MISSING from this loadout. Recipe is completely non-functional.

**Q4 Downstream Harm — HIGH**  
Wrong convergence/divergence signals cause agents to make bad strategic decisions. Could push economy toward the very monoculture it claims to prevent.

**Overall: CRITICAL** — Recipe non-functional. Needs both lenses installed first.

---

### CRITICAL-3: inversion_second_order_recipe.md — Both ingredient lenses missing from loadout

**Q1 Input Fragility — MED**  
Stage 1 assumes problem input has "explicit constraints" — if the problem description is vague, Stage 1 produces nothing useful. No fallback.

**Q2 Trust Abuse — MED**  
Stage 3 synthesis scores by "constraint_depth × second_order_coverage" — both are unvalidated subjective scores. An agent could tune inputs to produce any desired "final reframe."

**Q3 Compositional Gaps — CRITICAL**  
`constraint_inversion_lens` and `second_order_lens` are BOTH MISSING from loadout. Recipe is non-functional.

**Q4 Downstream Harm — MED**  
A plausible-sounding reframe could mislead agents into solving the wrong problem. Wrong direction compounds over rounds.

**Overall: CRITICAL** — Recipe non-functional. Both ingredient lenses missing.

---

### CRITICAL-4: q_recipe_chain.md — Reward extraction is text-parsed and gameable

**Q1 Input Fragility — MED**  
The quest file uses `## Reward` as human-readable text. If formatted as `## Reward\n100 gold` the regex in execute.sh works. Any other formatting could misparse.

**Q2 Trust Abuse — MED**  
Agent can view the quest template before accepting. They know the reward amount in advance — no information asymmetry.

**Q3 Compositional Gaps — MED**  
Template quest vs agent's local copy: if template is modified AFTER acceptance, the reward extraction still works. But the template should be immutable once quest is active.

**Q4 Downstream Harm — CRITICAL**  
The execute.sh reward extraction uses `grep -oE '[0-9]+' | head -1`. If the quest file contains multiple numbers anywhere (e.g., "## Reward\n100 gold\n## Version 1.1"), the FIRST number is extracted. This is fragile — a template editor could accidentally reorder fields.  
More critically: the extraction logic says `REWARD="${REWARD:-50}"` as fallback. If grep finds no number, it defaults to 50. An agent could exploit a misconfigured quest file to always get 50g even for a 120g quest.

**Overall: CRITICAL** — Reward extraction is text-parsed, not structure-verified. Recommend using a structured field like `reward_gold: 120` instead of relying on grep of human-readable text.

---

## HIGH FINDINGS (should be addressed)

---

### HIGH-1: loadout_dependency_proof_recipe.md — test_skill output is forgeable

**Q1 Input Fragility — MED**  
Recipe trusts its own audit output. What audits the auditor? No self-referential check.

**Q2 Trust Abuse — HIGH**  
The recipe trusts `test_result` from test_skill — but test_skill produces forgeable JSON records (audit_bug_exploit). An agent could forge a passing test result, then run this recipe and have it "verify" the forged result.

**Q3 Compositional Gaps — HIGH**  
"cycle_risk" detection uses pattern matching — could miss subtle cycles involving 3+ skills. A cycle where A→B→C→A would not be caught by simple pairwise checks.

**Q4 Downstream Harm — HIGH**  
A skill that passes this proof could still be broken if test_skill's result was forged. The "proof" gives false confidence. Worse: it's in loadout, so agents will trust it.

**Overall: HIGH** — Patch recommendation: integrate `signed_test_chain_recipe` into this recipe so test_skill output is HMAC-verified before being trusted.

---

### HIGH-2: signed_test_chain_recipe.md — Secret key management flaw

**Q1 Input Fragility — MED**  
If secret_key is empty string, all HMAC signatures are computed with empty key — trivially reproducible by any observer.

**Q2 Trust Abuse — HIGH**  
The secret_key is passed as a CLI parameter — it appears in process lists, shell history, and log files. Anyone with read access to the agent's environment can extract the key and forge test records.

**Q3 Compositional Gaps — MED**  
If test_skill is absent or produces non-JSON output, the jq pipeline fails. The recipe does not handle this gracefully.

**Q4 Downstream Harm — HIGH**  
Even with a valid HMAC signature, if the underlying test was run with wrong or adversarial input, the signed record certifies the wrong result. The signature proves execution happened, but not that the execution was correct.

**Overall: HIGH** — Recommend: use environment variable (not CLI arg) for secret_key, and bind the skill_path + input_hash into the signed record more tightly.

---

### HIGH-3: divergence_corrector_recipe.md — Prescription could trigger unintended game actions

**Q1 Input Fragility — MED**  
Expects `economy_state` JSON with specific nested structure. Malformed JSON → jq fails or produces garbage. Recipe doesn't validate economy_state schema before processing.

**Q2 Trust Abuse — MED**  
If `agent_001` or `agent_002` fields are missing from economy_state, the prescription is still emitted (null values propagate through). No null-check guards.

**Q3 Compositional Gaps — MED**  
Uses `dependency_trace_lens` which itself has Q3 issues (orphan claims unvalidated). Chain of untrusted data: each step amplifies the previous error.

**Q4 Downstream Harm — HIGH**  
The "immediate" prescription actions include `post_quest_bounty` and `buyer_subsidy` — these reference game mechanics that may not exist or may have unintended side effects. If the prescription says "give agent_002 50g" but agent_002 doesn't exist in game state, what happens?

**Overall: HIGH** — Validate economy_state schema before processing. Add guard rails on prescription actions.

---

### HIGH-4: test_skill.md — Output is unvalidated, forgeable

**Q1 Input Fragility — MED**  
Very large skill files or extremely long test_input strings could cause the "fresh Claude instance" to timeout or produce truncated output.

**Q2 Trust Abuse — MED**  
The test record is written to a JSON file that can be read and rewritten by any agent with filesystem access. No write protection.

**Q3 Compositional Gaps — HIGH**  
Test_skill is referenced BY MANY loadout recipes as a dependency (loadout_dependency_proof_recipe, signed_test_chain_recipe). But test_skill's output is forgeable. If test_skill output is forged, all recipes that depend on it produce false results.

**Q4 Downstream Harm — HIGH**  
A forged test record that claims "pass" enables a broken skill to be listed as verified. Buyers lose gold. This is the core exploit documented in `audit_bug_exploit`.

**Overall: HIGH** — Note: this is the exploit documented in standing rules. The fix is `signed_test_chain_recipe` which must be installed alongside test_skill.

---

## MED FINDINGS (noted, lower priority)

| Skill | Q1 | Q2 | Q3 | Q4 | Notes |
|---|---|---|---|---|---|
| dependency_trace_lens | MED | MED | MED | MED | `orphaned` field unvalidated; hub_score is self-claimed |
| market_diversity_lens | MED | MED | MED | MED | Empty board → false positives on all types missing; recommendation field is free text |
| rarity_guard_lens | MED | MED | MED | MED | Doesn't actually enforce rarity — only describes structure; seller can still inflate |
| skill_template | LOW | MED | LOW | MED | Downstream: bad template → bad skills; no rarity enforcement in template |
| stasis_breaker_recipe | MED | MED | MED | MED | game.json may not be accessible in all contexts; action injection could be blocked silently |
| convergence_breaker_recipe | HIGH | HIGH | CRITICAL | HIGH | Already listed as CRITICAL-2 above |

## LOW/INFO FINDINGS

| Skill | Notes |
|---|---|
| q_forge_lens | No exploitable structure; lens skill is self-contained; reward is straightforward |
| skill_template | Common rarity, limited blast radius; downstream compounding possible but low probability |

---

## Recommended Fix Priority

1. **[CRITICAL]** Install `divergence_lens` and `convergence_lens` → enables `chain_verifier_recipe` and `convergence_breaker_recipe`
2. **[CRITICAL]** Change quest reward extraction from text-parsing to structured field (`reward_gold: 120`)
3. **[HIGH]** Integrate `signed_test_chain_recipe` into `loadout_dependency_proof_recipe` — verify test_skill output before trusting it
4. **[HIGH]** Fix secret_key management in `signed_test_chain_recipe` — use env var, not CLI arg
5. **[MED]** Add schema validation for `economy_state` in `divergence_corrector_recipe`
6. **[MED]** Add self-referential check in `loadout_dependency_proof_recipe` (recipe auditing itself)
