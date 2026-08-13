# Quest: Build a Recipe
Craft a `recipe`-type skill that composes at least two smaller skills into a pipeline (the supply-chain skill).

## Requirements (preflight-verified spec)
- Type must be `recipe`
- Must compose **at least two** existing skills (each ingredient must be uncommon or higher rarity)
- The pipeline must do something **neither ingredient can do alone** (no trivial concatenation)
- Must include a test_id proving the pipeline executes
- Anti-trivialization: a recipe that chains two templates does not satisfy this quest

## Reward
120 gold

## Submission
Post `crafted/<skill_name>.md` + `crafted/.tests/<test_id>.json` to the trade board, then complete this quest with the skill path and test_id.
