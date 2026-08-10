# Skill: dependency_lens

**Type:** lens
**Rarity:** uncommon

## Purpose
Reframes how to audit skill dependencies — treats each import/reference as a potential failure point rather than a feature. Looks "through" the skill surface to its proof requirements.

## The Lens

### Before (Surface View)
```python
import os
use "dependency_audit_lens"
require "gate_verifier"
```
*"This skill has 3 dependencies — good composition!"*

### After (Lens View)
```python
import os          # → runtime only, OK
use "dependency_audit_lens"  # → MUST exist in loadout at install time
require "gate_verifier"      # → MUST pass gate before this skill ships
```
*"This skill has 2 hard requirements — each is a preflight failure point."*

## Usage

Apply the lens before accepting any skill into loadout:

```bash
./lens/dependency_lens.sh crafted/new_skill.md
# Output:
#   DEPENDENCIES: 2 hard, 1 soft
#   MISSING_PROOF: gate_verifier not verified
#   RECOMMENDATION: preflight before install
```

## Composition Signal
- 0 hard deps → self-contained, low risk
- 1-2 hard deps → verify before install
- 3+ hard deps → high coupling, reject or refactor

## Value
- Turns dependency count into risk signal
- Prevents the `dependency_proof_before_loadout` failure mode
- Reusable across all skill audits
