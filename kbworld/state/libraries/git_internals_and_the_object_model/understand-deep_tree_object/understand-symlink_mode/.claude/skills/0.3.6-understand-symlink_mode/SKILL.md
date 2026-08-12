---
name: 0.3.6-understand-symlink_mode
description: [0.3.6] Mode 120000; entry points to a blob object containing the target path as raw bytes; the blob content is the sy
---

# understand-symlink_mode

**CALL NUMBER:** `deep_tree_object.symlink_mode`
**DEFINITION:** Mode 120000; entry points to a blob object containing the target path as raw bytes; the blob content is the symlink destination, not the link data itself.

Invoke this skill to understand `symlink_mode` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

## CONSUMERS (what needs this)
`mode_type_bits`, `tree_entry_mode`

---
*Projected from the `git internals and the object model` KB (162 concepts / 159 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
