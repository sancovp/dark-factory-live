# understand-tree_object

**CALL NUMBER:** `git_internals_and_the_object_model.tree_object : deep_commit_object(8), deep_tree_object(8)`
**DEFINITION:** Type-2 git object listing directory entries as (mode, name, sha1) tuples; represents a single directory snapshot at a point in time.

Invoke this skill to understand `tree_object` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_commit_object`
- **commit_message_encoding_encoding_header** (d2): Optional header line 'encoding <encoding-name>' in a commit object's raw text; git stores whatever the user wrote verbatim.
- **commit_message_encoding_encoding_value** (d3): The character encoding name stored in the encoding header (UTF-8, ISO-8859-1, Windows-1252, etc.); controls byte-to-character interpretation of the message bytes.
- **commit_message_encoding_message_bytes** (d4): Raw byte sequence forming the commit message body; decoded using encoding_value (or assumed UTF-8) to produce display characters.
- **commit_message_encoding_original_encoding** (d4): Alias for encoding_value; the encoding recorded at commit time distinguishing the message's original byte interpretation from the display encoding.
- **commit_message_encoding_transcoding_logic** (d4): git's internal conversion from the stored encoding_value to the requested log_encoding_flag encoding; uses iconv-style conversion with loss handling.
- **commit_message_encoding_encoding_fallback** (d5): Fallback behavior when transcoding_logic cannot map a character; typically replaces with a substitution character or skips the byte.
- **commit_message_encoding_transcoded_message** (d5): The output of transcoding_logic: message_bytes decoded then re-encoded into log_encoding_flag; git log emits this to the terminal.
- **commit_message_encoding_display_encoding** (d6): The terminal or output stream encoding git uses when writing the transcoded_message; git assumes UTF-8 output if terminal encoding is unset.

### from `deep_tree_object`
- **executable_file_mode** (d2): Mode 100755; regular file with execute bits set; Git marks it this way to preserve the executable bit across platforms that handle it differently.
- **mode_bit_format** (d2): Base-8 positional numeral system used to encode file mode; Git stores exactly 6 octal digits representing 18 bits of mode information.
- **mode_permission_bits** (d2): The lower 9 bits (three octal digits) encoding Unix owner/group/other read-write-execute permissions; displayed as the last three digits of the 6-digit octal mode.
- **mode_type_bits** (d2): The upper bits of the octal mode identifying the entry's object category: regular file, directory, symlink, or submodule; encoded in the first two octal digits.
- **regular_file_mode** (d2): Mode 100644; standard blob-backed file with read permission for all and write for owner; the default for non-executable files committed to Git.
- **subtree_mode** (d2): Mode 040000; entry points to a nested tree object representing a directory; the tree entry name contains a forward slash but the slash is not stored in the entry itself.
- **symlink_mode** (d2): Mode 120000; entry points to a blob object containing the target path as raw bytes; the blob content is the symlink destination, not the link data itself.
- **mode_zero_padding** (d3): The leading zero in modes like 100644 and 040000 ensures consistent 6-digit width; the zero fills the third octal digit reserved for special file type flags.

### from `git_internals_and_the_object_model`
- **object_type_inspection** (d1): git cat-file -t reveals object type; git cat-file -s shows byte size; git cat-file -p pretty-prints content; git rev-list walks commit graph.
- **submodule_pointer** (d1): Entry in a parent repository's tree object referencing a specific commit of a nested repository; stored as mode 160000 with commit SHA-1.
- **tree_entry_mode** (d1): Octal mode in tree object: 100644 (regular file), 100755 (executable), 040000 (subtree), 120000 (symlink), 160000 (submodule).
- **tree_entry_name** (d1): Null-terminated byte string within tree entry; may contain slash for subdirectory entries; case-sensitive on all platforms.
- **commit_filter** (d2): Revision traversal predicate (--since, --author, --grep, --S, --G) restricting which commits appear in output.

## CONSUMERS (what needs this)
`blob_object`, `index_file`, `merkle_tree_property`, `recursive_strategy`, `sha1_hash`, `subtree_strategy`

---
*Projected from the `git internals and the object model` KB (162 concepts / 159 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*