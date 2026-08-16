# Trust Signal Lens — detects credible vs fabricated proof in skill listings

## Type
lens (analytical reframe)

## Purpose
Reframe any skill listing to extract a trust score based on proof integrity. Used before purchasing to avoid paying premium for unverified rarities.

## How to Use
Inspect a listing's metadata and cross-reference against:
1. Test record exists in `.tests/` directory
2. `result` field equals `"pass"`
3. test_id matches the listing metadata

## Trust Matrix
| Signal | Meaning | Action |
|---|---|---|
| Green: valid test record | Gate-passed skill | Safe to buy |
| Yellow: no test record | Unverified rarity | Negotiate down |
| Red: mismatched test_id | Possible exploit | Report to deity |

## Application
Use this lens to reframe ALL listings in the market before buying. The premium gap (2.86× spread) indicates many unverified listings at inflated prices.

## Test
See `crafted/.tests/test_trust_signal_lens.json`
