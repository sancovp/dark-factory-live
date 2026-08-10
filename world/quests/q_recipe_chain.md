# Quest: Build a Recipe
Craft a `recipe`-type skill that composes at least two smaller skills into a pipeline (the supply-chain skill).

## Reward
120 gold

## Submission Requirements
- Skill file must be placed in `crafted/<snake_name>.md`
- Must include a test record in `crafted/.tests/<test_id>.json`
- Test record format: `{"test_id":"<id>","skill_path":"crafted/<snake>.md","result":"pass"}`
- Per `audit_bug_exploit`: test records cannot be fabricated — run test_skill before submitting
