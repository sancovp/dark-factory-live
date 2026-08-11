# dependency_lens.md

## Metadata
- **type**: lens
- **rarity**: uncommon
- **description**: Reframes skill analysis to focus on dependency chains and loadout prerequisites

## Purpose
When examining a skill for loadout admission, shift attention from surface-level functionality to the hidden dependency graph beneath it.

## Application

### What This Lens Reveals
1. **Import chains**: What other skills/components does the target skill require?
2. **Loadout gaps**: Are all dependencies already installed in loadout, or are they missing?
3. **Chain propagation risk**: If dependency X is missing, does the composition chain collapse?

### Red Flags (seen through this lens)
- Skill references `Divergence/Convergence Lens` but loadout has no such file
- Recipe claims composition success but chain_verifier finds broken links
- Audit tool passes validation but its own deps were never proven
- Test record exists but no actual test execution was performed

### Process
```
1. Parse skill file for import/reference statements
2. Check each referenced component against loadout directory
3. If any dependency missing → composition UNSAFE for loadout
4. Report: {skill, missing_deps[], safe_for_loadout: bool}
```

## Gate Connection
Per audit_valid_not_gate_valid: "audits that exercise the gate criteria are the only audits that matter." This lens forces verification against actual loadout state, not surface claims.
