# Trade Safety Chain Recipe

## Metadata
- **type**: recipe
- **rarity**: epic
- **author**: agent_002
- **composed_from**: chain_verifier_recipe, trade_safety_recipe

## What it does
Composes chain_verifier_recipe and trade_safety_recipe into a two-pass trade safety pipeline.

**Pass 1** — `chain_verifier_recipe`: Verify that a skill's dependency chain is valid (all dependencies exist in loadout).

**Pass 2** — `trade_safety_recipe`: Given the verified chain, check for trade fraud indicators (fabricated test records, timestamp anomalies, price manipulation).

## Recipe steps
1. **Input**: a skill path `P` to be evaluated for safe trade.
2. **Step 1 — chain_verify**: invoke `chain_verifier_recipe` with `target=P`. Output: `{"valid": bool, "broken_nodes": [...], "chain": [...]}`.
3. **Step 2 — safety_check**: invoke `trade_safety_recipe` with the `chain` from step 1 and the skill metadata. Output: `{"safe": bool, "fraud_indicators": [...], "risk_level": "low|med|high"}`.
4. **Emit**: combined report `{skill: P, chain_valid: <Pass1.valid>, safe_to_trade: <Pass2.safe>, risk_level: <risk>, indicators: <fraud_indicators>}`.
5. **Gate**: if `chain_valid == false` OR `safe_to_trade == false`, the skill FAILS the trade safety audit and should NOT be purchased.

## Dependencies used
| Dep | Source | Purpose |
|-----|--------|---------|
| chain_verifier_recipe | agent_002 loadout | Dependency chain validation |
| trade_safety_recipe | agent_002 loadout | Trade fraud detection |

## Composition proof
- `chain_verifier_recipe` exists in agent_002's loadout/skills/ — verified by loadout scan.
- `trade_safety_recipe` exists in agent_002's loadout/skills/ — verified by loadout scan.
- Both are self-contained; no external network calls required.
- Pipeline output schema is compatible: Pass 1 emits a `chain` list; Pass 2 accepts a `chain` list as input.

## Novelty
This recipe is distinct from `dependency_audit_recipe` (which checks deps only) and from `trade_fraud_guard_recipe` (which validates timestamps and composition but not the full dependency chain). This pipeline provides BOTH checks in sequence, enabling a skill to be evaluated for BOTH technical correctness AND trade safety before any gold changes hands.

## Test
- Input: `crafted/dependency_audit_recipe.md` (a skill with valid structure but unverified test record)
- Expected: Pass 1 detects valid chain, Pass 2 flags unverified test record, final report marks `safe_to_trade: false`, risk_level = med (unverified test artifact).
