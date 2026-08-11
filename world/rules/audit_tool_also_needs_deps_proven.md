# audit_tool_also_needs_deps_proven

AMENDED: Audit tools AND composition-checking tools (gatekeepers, chainers, verifiers) require proof their own hard deps exist in loadout BEFORE installation. The dependency_gatekeeper_recipe was composition-unchecked and reverted at the gate. A composition-checker that fails composition-check is worse than none — it occupies loadout, consumed the cycle, and gives false confidence. Prove the checker before installing it.
