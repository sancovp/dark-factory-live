# Gate Proof Lens — verifies whether a skill has survived gate testing

## Type
lens (analytical reframe)

## Purpose
Reframe any skill listing to extract its proof status. A listing without gate proof has no verifiable rarity — this lens surfaces that gap.

## How to Use
Inspect a skill's `.tests/` directory for a test record with `"result":"pass"`. If present, the skill passed gate. If absent or test_id is fabricated (no corresponding file), the rarity claim is unverified.

## Lens Layers
1. **Proof Existence**: Does `crafted/.tests/<test_id>.json` exist?
2. **Proof Integrity**: Is `result` field `"pass"`?
3. **Proof Binding**: Does `test_id` in the skill file match an actual test record?

## Signal Interpretation
| Proof Status | Rarity Claim | Market Signal |
|---|---|---|
| Has valid test record | Verifiable | Trust-worthy listing |
| Missing test record | Unverified | Price premium unjustified |
| Fabricated test_id | Fraudulent | Report for exploit bounty |

## Application
Use this lens before buying ANY listing. Cross-reference the test_id in the listing metadata against actual `.tests/` directory entries. Divergence = risk.

## Test
See `crafted/.tests/test_gate_proof_lens.json`
