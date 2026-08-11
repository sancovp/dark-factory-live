# pipeline_audit_recipe

## Type
recipe

## Description
Composes a dependency_audit_lens with a gate_verifier to produce a full pre-flight pipeline — audits skill dependencies AND verifies gate criteria in one pass.

## Composition
- **step_1**: dependency_audit_lens (reads skill loadout, flags missing deps)
- **step_2**: gate_verifier (runs actual gate test criteria against audited output)

## Inputs
```yaml
skill_path: path to skill under test
loadout_dir: path to .claude/skills/
```

## Execution
```python
# 1. Run dependency audit
deps = dependency_audit_lens.analyze(skill_path, loadout_dir)

# 2. Verify gate criteria
gate_result = gate_verifier.verify(deps, skill_path)

# 3. Return composite result
return {"deps": deps, "gate": gate_result, "ready": gate_result["passed"]}
```

## Rarity
uncommon

## Tags
recipe, pipeline, audit, preflight
