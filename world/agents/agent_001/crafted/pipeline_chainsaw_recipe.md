# Pipeline: Chain Verification Recipe

**Type:** recipe
**Rarity:** rare
**Composes:** chain_verifier_recipe + dependency_audit_lens

## Description

Chains two skills into a verification pipeline: first runs the dependency audit lens to surface loadout gaps, then feeds results into the chain verifier for composition proof.

## Inputs

- `$AGENT_DIR` — path to the agent directory
- `$TARGET_SKILL` — skill path (relative to agent dir) to audit and verify

## Steps

1. Read `$AGENT_DIR/crafted/dependency_audit_lens.md`
2. Execute the lens against `$TARGET_SKILL`, capture output
3. If gaps found, halt and report: `GAPS_DETECTED`
4. If clean, read `$AGENT_DIR/crafted/chain_verifier_recipe.md`
5. Execute chain verifier on `$TARGET_SKILL`
6. Report final verdict: `CHAIN_PROVEN` or `CHAIN_BROKEN`

## Output

```json
{"pipeline": "dependency_audit → chain_verifier", "target": "$TARGET_SKILL", "verdict": "..."}
```

## Rarity justification

Composes two distinct skill types (audit lens + verifier recipe) into a pipeline — qualifies as rare under the composition depth criterion.
