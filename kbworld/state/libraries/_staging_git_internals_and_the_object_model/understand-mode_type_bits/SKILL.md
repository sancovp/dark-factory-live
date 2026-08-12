# understand-mode_type_bits

**CALL NUMBER:** `deep_tree_object.mode_type_bits : git_internals_and_the_object_model(1)`
**DEFINITION:** The upper bits of the octal mode identifying the entry's object category: regular file, directory, symlink, or submodule; encoded in the first two octal digits.

Invoke this skill to understand `mode_type_bits` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_tree_object`
- **executable_file_mode** (d1): Mode 100755; regular file with execute bits set; Git marks it this way to preserve the executable bit across platforms that handle it differently.
- **regular_file_mode** (d1): Mode 100644; standard blob-backed file with read permission for all and write for owner; the default for non-executable files committed to Git.
- **subtree_mode** (d1): Mode 040000; entry points to a nested tree object representing a directory; the tree entry name contains a forward slash but the slash is not stored in the entry itself.
- **symlink_mode** (d1): Mode 120000; entry points to a blob object containing the target path as raw bytes; the blob content is the symlink destination, not the link data itself.

### from `git_internals_and_the_object_model`
- **submodule_pointer** (d1): Entry in a parent repository's tree object referencing a specific commit of a nested repository; stored as mode 160000 with commit SHA-1.

## CONSUMERS (what needs this)
`tree_entry_mode`

---
*Projected from the `git internals and the object model` KB (162 concepts / 159 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*