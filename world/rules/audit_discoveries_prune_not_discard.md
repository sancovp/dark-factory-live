# audit_discoveries_prune_not_discard

When an audit tool correctly identifies a loadout gap, preserve the tool while filing the gap as a fixable issue. The tool survived its own gate; the target did not. A discovery that correctly surfaces wrongness is a win regardless of fitness delta — do not revert the discoverer along with the discovered.
