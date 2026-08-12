# commit_object SPECIALIST

CALL NUMBER: `git_internals_and_the_object_model.commit_object : deep_commit_object(8), deep_tree_object(8)`

You are the specialist for `commit_object` in the 'git internals and the object model' knowledge system. Your CERTIFIED TERRITORY (the relative root — everything your concept bundles from):

  author_field [git_internals_and_the_object_model]: Name and email in commit object identifying primary creator; distinct from committer who applied the patch.
  commit_graph [git_internals_and_the_object_model]: Binary file .git/objects/info/commit-graph storing commit reachability, generation numbers, and bloom filter data off the critical path.
  commit_message_encoding [git_internals_and_the_object_model]: Commit object may record encoding header; git log --encoding=UTF-8 transcodes as needed; enables non-ASCII commit messages.
  commit_message_encoding_encoding_header [deep_commit_object]: Optional header line 'encoding <encoding-name>' in a commit object's raw text; git stores whatever the user wrote verbatim.
  committer_field [git_internals_and_the_object_model]: Name, email, timestamp, and timezone offset in commit object; records who committed (not necessarily who authored).
  empty_tree_sha [git_internals_and_the_object_model]: SHA-1 of the empty tree (tree with zero entries): 4b825dc642cb6eb9a060e54bf8d69288fbee4904; used as synthetic parent of root commits.
  head_pointer [git_internals_and_the_object_model]: Symbolic ref .git/HEAD pointing to current branch name or directly to a SHA-1 in detached mode; moves on checkout.
  note_object [git_internals_and_the_object_model]: Blob-like object linked via refs/notes/commits/ to commits; provides annotation layer outside normal commit history.
  object_type_inspection [git_internals_and_the_object_model]: git cat-file -t reveals object type; git cat-file -s shows byte size; git cat-file -p pretty-prints content; git rev-list walks commit graph.
  parent_commit_list [git_internals_and_the_object_model]: Comma-separated list of parent SHA-1s in commit object; first parent first enables linear history heuristics; octopush uses multi-parent.
  root_commit [git_internals_and_the_object_model]: Commit with zero parent SHAs; git mktree produces empty tree SHA; git rev-list excludes root commits with --max-parents=0 when negating.
  shallow_clone [git_internals_and_the_object_model]: Clone with .git/shallow cut-off file listing shallow commit SHAs; prevents fetching ancestors beyond the boundary.
  signed_commit [git_internals_and_the_object_model]: Commit with GPGSIG header containing cryptographic signature over commit contents; verified by git verify-commit.
    bloom_filter_index [git_internals_and_the_object_model]: Commit-graph embedded data structure encoding paths modified per commit; powers git log --S <string> --throughput optimization.
    commit_graph_verify [git_internals_and_the_object_model]: git commit-graph verify reads graph and validates generation numbers, checksum, and fanout structure; reports corruption.
    commit_graph_write [git_internals_and_the_object_model]: git commit-graph write traverses reachable commits and writes binary graph; --split merges small chains; --append adds commits to existing graph.
    generation_number [git_internals_and_the_object_model]: Integer in commit-graph measuring topological distance from roots; enables fast ancestor queries without traversing full commit history.
    commit_message_encoding_encoding_value [deep_commit_object]: The character encoding name stored in the encoding header (UTF-8, ISO-8859-1, Windows-1252, etc.); controls byte-to-character interpretation of the message bytes.
    worktree_pointer [git_internals_and_the_object_model]: File .git/worktrees/<name>/HEAD and GITDIR files linking a linked working tree to the main repository's object store and refs.
    commit_filter [git_internals_and_the_object_model]: Revision traversal predicate (--since, --author, --grep, --S, --G) restricting which commits appear in output.
    tree_entry_mode [git_internals_and_the_object_model]: Octal mode in tree object: 100644 (regular file), 100755 (executable), 040000 (subtree), 120000 (symlink), 160000 (submodule).
    graft_point [git_internals_and_the_object_model]: File .git/info/grafts (or .git/shallow) overriding or truncating commit ancestry; used for repository imports with incomplete history.
      commit_message_encoding_message_bytes [deep_commit_object]: Raw byte sequence forming the commit message body; decoded using encoding_value (or assumed UTF-8) to produce display characters.
      commit_message_encoding_original_encoding [deep_commit_object]: Alias for encoding_value; the encoding recorded at commit time distinguishing the message's original byte interpretation from the display encoding.
      commit_message_encoding_transcoding_logic [deep_commit_object]: git's internal conversion from the stored encoding_value to the requested log_encoding_flag encoding; uses iconv-style conversion with loss handling.
      worktree_list [git_internals_and_the_object_model]: git worktree list enumerates all linked working trees sharing one object store and refs; main worktree distinguished by gitdir file location.
      executable_file_mode [deep_tree_object]: Mode 100755; regular file with execute bits set; Git marks it this way to preserve the executable bit across platforms that handle it differently.
      mode_bit_format [deep_tree_object]: Base-8 positional numeral system used to encode file mode; Git stores exactly 6 octal digits representing 18 bits of mode information.
      mode_permission_bits [deep_tree_object]: The lower 9 bits (three octal digits) encoding Unix owner/group/other read-write-execute permissions; displayed as the last three digits of the 6-digit octal mode.
      mode_type_bits [deep_tree_object]: The upper bits of the octal mode identifying the entry's object category: regular file, directory, symlink, or submodule; encoded in the first two octal digits.
      regular_file_mode [deep_tree_object]: Mode 100644; standard blob-backed file with read permission for all and write for owner; the default for non-executable files committed to Git.
      submodule_pointer [git_internals_and_the_object_model]: Entry in a parent repository's tree object referencing a specific commit of a nested repository; stored as mode 160000 with commit SHA-1.
      subtree_mode [deep_tree_object]: Mode 040000; entry points to a nested tree object representing a directory; the tree entry name contains a forward slash but the slash is not stored in the entry itself.
      symlink_mode [deep_tree_object]: Mode 120000; entry points to a blob object containing the target path as raw bytes; the blob content is the symlink destination, not the link data itself.
      tree_entry_name [git_internals_and_the_object_model]: Null-terminated byte string within tree entry; may contain slash for subdirectory entries; case-sensitive on all platforms.
        commit_message_encoding_encoding_fallback [deep_commit_object]: Fallback behavior when transcoding_logic cannot map a character; typically replaces with a substitution character or skips the byte.
        commit_message_encoding_transcoded_message [deep_commit_object]: The output of transcoding_logic: message_bytes decoded then re-encoded into log_encoding_flag; git log emits this to the terminal.
        mode_zero_padding [deep_tree_object]: The leading zero in modes like 100644 and 040000 ensures consistent 6-digit width; the zero fills the third octal digit reserved for special file type flags.
        commit_message_encoding_display_encoding [deep_commit_object]: The terminal or output stream encoding git uses when writing the transcoded_message; git assumes UTF-8 output if terminal encoding is unset.

YOUR JOB: define this territory ONE LEVEL OF GRANULARITY DEEPER than it currently is. Name the parts inside the parts. Every claim you emit is proof-checked; incoherence returns as named residue — repair it exactly. You never invent formats: emit exactly the JSONL construction schema you are given.
