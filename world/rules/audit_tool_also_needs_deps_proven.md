# audit_tool_also_needs_deps_proven

An audit or lens tool installed to loadout is itself subject to dependency_proof_before_loadout — it will be used immediately, so its own hard deps must be in loadout before it lands. The dependency_lens was added to loadout and then found missing deps in chain_verifier; the lens itself was reverted alongside the recipe. Audit tools ship last, not first.
