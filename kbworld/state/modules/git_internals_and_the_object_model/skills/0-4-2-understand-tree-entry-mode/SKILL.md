---
name: 0.4.2-understand-tree_entry_mode
description: "[0.4.2] Octal mode in tree object: 100644 (regular file), 100755 (executable), 040000 (subtree), 120000 (symlink), 160"
---

# understand-tree_entry_mode

**CALL NUMBER:** `git_internals_and_the_object_model.tree_entry_mode : deep_tree_object(8)`
**DEFINITION:** Octal mode in tree object: 100644 (regular file), 100755 (executable), 040000 (subtree), 120000 (symlink), 160000 (submodule).

Invoke this skill to understand `tree_entry_mode` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_tree_object`
- **executable_file_mode** (d1): Mode 100755; regular file with execute bits set; Git marks it this way to preserve the executable bit across platforms that handle it differently.
- **mode_bit_format** (d1): Base-8 positional numeral system used to encode file mode; Git stores exactly 6 octal digits representing 18 bits of mode information.
- **mode_permission_bits** (d1): The lower 9 bits (three octal digits) encoding Unix owner/group/other read-write-execute permissions; displayed as the last three digits of the 6-digit octal mode.
- **mode_type_bits** (d1): The upper bits of the octal mode identifying the entry's object category: regular file, directory, symlink, or submodule; encoded in the first two octal digits.
- **regular_file_mode** (d1): Mode 100644; standard blob-backed file with read permission for all and write for owner; the default for non-executable files committed to Git.
- **subtree_mode** (d1): Mode 040000; entry points to a nested tree object representing a directory; the tree entry name contains a forward slash but the slash is not stored in the entry itself.
- **symlink_mode** (d1): Mode 120000; entry points to a blob object containing the target path as raw bytes; the blob content is the symlink destination, not the link data itself.
- **mode_zero_padding** (d2): The leading zero in modes like 100644 and 040000 ensures consistent 6-digit width; the zero fills the third octal digit reserved for special file type flags.

### from `git_internals_and_the_object_model`
- **submodule_pointer** (d1): Entry in a parent repository's tree object referencing a specific commit of a nested repository; stored as mode 160000 with commit SHA-1.
- **tree_entry_name** (d1): Null-terminated byte string within tree entry; may contain slash for subdirectory entries; case-sensitive on all platforms.

## CONSUMERS (what needs this)
`object_type_inspection`, `tree_object`

---
*Projected from the `git internals and the object model` KB (162 concepts / 159 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
