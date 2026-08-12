---
name: 0.4.6-understand-blob_object
description: [0.4.6] Type-1 git object storing raw file contents verbatim; identified by SHA-1 of content; no filename or metadata 
---

# understand-blob_object

**CALL NUMBER:** `git_internals_and_the_object_model.blob_object : deep_commit_object(8), deep_tree_object(8)`
**DEFINITION:** Type-1 git object storing raw file contents verbatim; identified by SHA-1 of content; no filename or metadata retained.

Invoke this skill to understand `blob_object` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

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
- **executable_file_mode** (d3): Mode 100755; regular file with execute bits set; Git marks it this way to preserve the executable bit across platforms that handle it differently.
- **mode_bit_format** (d3): Base-8 positional numeral system used to encode file mode; Git stores exactly 6 octal digits representing 18 bits of mode information.
- **mode_permission_bits** (d3): The lower 9 bits (three octal digits) encoding Unix owner/group/other read-write-execute permissions; displayed as the last three digits of the 6-digit octal mode.
- **mode_type_bits** (d3): The upper bits of the octal mode identifying the entry's object category: regular file, directory, symlink, or submodule; encoded in the first two octal digits.
- **regular_file_mode** (d3): Mode 100644; standard blob-backed file with read permission for all and write for owner; the default for non-executable files committed to Git.
- **subtree_mode** (d3): Mode 040000; entry points to a nested tree object representing a directory; the tree entry name contains a forward slash but the slash is not stored in the entry itself.
- **symlink_mode** (d3): Mode 120000; entry points to a blob object containing the target path as raw bytes; the blob content is the symlink destination, not the link data itself.
- **mode_zero_padding** (d4): The leading zero in modes like 100644 and 040000 ensures consistent 6-digit width; the zero fills the third octal digit reserved for special file type flags.

### from `git_internals_and_the_object_model`
- **object_type_inspection** (d1): git cat-file -t reveals object type; git cat-file -s shows byte size; git cat-file -p pretty-prints content; git rev-list walks commit graph.
- **partial_clone** (d1): Clone with --filter omitting blob objects from transfer; missing blobs retrieved on demand via fetch-object; enables huge-repository workflows.
- **tree_object** (d1): Type-2 git object listing directory entries as (mode, name, sha1) tuples; represents a single directory snapshot at a point in time.
- **commit_filter** (d2): Revision traversal predicate (--since, --author, --grep, --S, --G) restricting which commits appear in output.
- **tree_entry_mode** (d2): Octal mode in tree object: 100644 (regular file), 100755 (executable), 040000 (subtree), 120000 (symlink), 160000 (submodule).
- **blob_prefetch** (d2): Git fetch-object or protocol v2 advertisements retrieving missing blob content on demand from partial clone; requires server support.
- **bundle_format** (d2): Self-contained .git-bundle file encoding ref updates and reachable objects; enables offline transfer via removable media.
- **promisor_ref** (d2): Reference in a partial clone marking an object as promised but not yet fetched; enables placeholder usage before physical retrieval.
- **submodule_pointer** (d2): Entry in a parent repository's tree object referencing a specific commit of a nested repository; stored as mode 160000 with commit SHA-1.
- **tree_entry_name** (d2): Null-terminated byte string within tree entry; may contain slash for subdirectory entries; case-sensitive on all platforms.
- **object_database** (d3): Directory-backed key-value store under .git/objects/; loose objects stored as zlib-deflated files keyed by SHA-1; packed objects aggregated into packfiles.
- **fsck_integrity** (d4): git fsck traverses all reachable objects validating SHA-1 linkage, ref integrity, and accessibility; reports dangling and unreachable.
- **loose_object** (d4): Individual compressed file stored at .git/objects/xx/xxxx...; fast to write but inefficient at scale; one object per file.
- **packfile** (d4): Single binary file consolidating many objects via delta compression; named pack-*.pack with companion .idx index; vastly reduces repository size.
- **delta_compression** (d5): Git's storage optimization encoding an object as a series of copy/insert commands relative to a base object; OFS_DELTA uses relative offsets; REF_DELTA uses absolute SHA-1.
- **packfile_bitmap** (d5): Reachability bitmap at packfile end enabling fast network transfer negotiation and clone/fetch optimization by marking all reachable objects.
- **packfile_index** (d5): Binary lookup table (.idx) enabling O(log n) SHA-1 to offset resolution within a packfile; also stores CRC-32 for integrity verification.
- **copy_instruction** (d6): Packfile command copying bytes from base object at offset+length; encodes file copy without recompression.
- **insert_instruction** (d6): Packfile command appending literal byte sequence to output; the raw new content not derivable from base.
- **ofs_delta** (d6): Delta format encoding base object as relative offset within packfile; safer for streaming than REF_DELTA which names base by SHA-1.
- **ref_delta** (d6): Delta format referencing base object by its SHA-1; simpler but requires base to precede delta in packfile or be separately reachable.
- **multi_pack_index** (d6): Compound .midx file spanning multiple packfiles; enables cross-pack object queries and accelerates repack scenarios.

## CONSUMERS (what needs this)
`byte_string_content`, `clean_filter`, `index_file`, `sha1_hash`, `smudge_filter`

---
*Projected from the `git internals and the object model` KB (162 concepts / 159 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
