---
name: 0.4.1-understand-commit_object
description: [0.4.1] Type-3 git object containing tree SHA, parent SHA(s), author, committer, timestamp, and message; forms the his
---

# understand-commit_object

**CALL NUMBER:** `git_internals_and_the_object_model.commit_object : deep_commit_object(8), deep_tree_object(8)`
**DEFINITION:** Type-3 git object containing tree SHA, parent SHA(s), author, committer, timestamp, and message; forms the history DAG backbone.

Invoke this skill to understand `commit_object` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `deep_commit_object`
- **commit_message_encoding_encoding_header** (d1): Optional header line 'encoding <encoding-name>' in a commit object's raw text; git stores whatever the user wrote verbatim.
- **commit_message_encoding_encoding_value** (d2): The character encoding name stored in the encoding header (UTF-8, ISO-8859-1, Windows-1252, etc.); controls byte-to-character interpretation of the message bytes.
- **commit_message_encoding_message_bytes** (d3): Raw byte sequence forming the commit message body; decoded using encoding_value (or assumed UTF-8) to produce display characters.
- **commit_message_encoding_original_encoding** (d3): Alias for encoding_value; the encoding recorded at commit time distinguishing the message's original byte interpretation from the display encoding.
- **commit_message_encoding_transcoding_logic** (d3): git's internal conversion from the stored encoding_value to the requested log_encoding_flag encoding; uses iconv-style conversion with loss handling.
- **commit_message_encoding_encoding_fallback** (d4): Fallback behavior when transcoding_logic cannot map a character; typically replaces with a substitution character or skips the byte.
- **commit_message_encoding_transcoded_message** (d4): The output of transcoding_logic: message_bytes decoded then re-encoded into log_encoding_flag; git log emits this to the terminal.
- **commit_message_encoding_display_encoding** (d5): The terminal or output stream encoding git uses when writing the transcoded_message; git assumes UTF-8 output if terminal encoding is unset.

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
- **author_field** (d1): Name and email in commit object identifying primary creator; distinct from committer who applied the patch.
- **commit_graph** (d1): Binary file .git/objects/info/commit-graph storing commit reachability, generation numbers, and bloom filter data off the critical path.
- **commit_message_encoding** (d1): Commit object may record encoding header; git log --encoding=UTF-8 transcodes as needed; enables non-ASCII commit messages.
- **committer_field** (d1): Name, email, timestamp, and timezone offset in commit object; records who committed (not necessarily who authored).
- **empty_tree_sha** (d1): SHA-1 of the empty tree (tree with zero entries): 4b825dc642cb6eb9a060e54bf8d69288fbee4904; used as synthetic parent of root commits.
- **head_pointer** (d1): Symbolic ref .git/HEAD pointing to current branch name or directly to a SHA-1 in detached mode; moves on checkout.
- **note_object** (d1): Blob-like object linked via refs/notes/commits/ to commits; provides annotation layer outside normal commit history.
- **object_type_inspection** (d1): git cat-file -t reveals object type; git cat-file -s shows byte size; git cat-file -p pretty-prints content; git rev-list walks commit graph.
- **parent_commit_list** (d1): Comma-separated list of parent SHA-1s in commit object; first parent first enables linear history heuristics; octopush uses multi-parent.
- **root_commit** (d1): Commit with zero parent SHAs; git mktree produces empty tree SHA; git rev-list excludes root commits with --max-parents=0 when negating.
- **shallow_clone** (d1): Clone with .git/shallow cut-off file listing shallow commit SHAs; prevents fetching ancestors beyond the boundary.
- **signed_commit** (d1): Commit with GPGSIG header containing cryptographic signature over commit contents; verified by git verify-commit.
- **bloom_filter_index** (d2): Commit-graph embedded data structure encoding paths modified per commit; powers git log --S <string> --throughput optimization.
- **commit_graph_verify** (d2): git commit-graph verify reads graph and validates generation numbers, checksum, and fanout structure; reports corruption.
- **commit_graph_write** (d2): git commit-graph write traverses reachable commits and writes binary graph; --split merges small chains; --append adds commits to existing graph.
- **generation_number** (d2): Integer in commit-graph measuring topological distance from roots; enables fast ancestor queries without traversing full commit history.
- **worktree_pointer** (d2): File .git/worktrees/<name>/HEAD and GITDIR files linking a linked working tree to the main repository's object store and refs.
- **commit_filter** (d2): Revision traversal predicate (--since, --author, --grep, --S, --G) restricting which commits appear in output.
- **tree_entry_mode** (d2): Octal mode in tree object: 100644 (regular file), 100755 (executable), 040000 (subtree), 120000 (symlink), 160000 (submodule).
- **graft_point** (d2): File .git/info/grafts (or .git/shallow) overriding or truncating commit ancestry; used for repository imports with incomplete history.
- **worktree_list** (d3): git worktree list enumerates all linked working trees sharing one object store and refs; main worktree distinguished by gitdir file location.
- **submodule_pointer** (d3): Entry in a parent repository's tree object referencing a specific commit of a nested repository; stored as mode 160000 with commit SHA-1.
- **tree_entry_name** (d3): Null-terminated byte string within tree entry; may contain slash for subdirectory entries; case-sensitive on all platforms.

## CONSUMERS (what needs this)
`cherry_pick_delta`, `merkle_tree_property`, `ours_strategy`, `rebase_replay`, `revert_delta`, `sha1_hash`

---
*Projected from the `git internals and the object model` KB (162 concepts / 159 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
