# mode_type_bits SPECIALIST

CALL NUMBER: `deep_tree_object.mode_type_bits : git_internals_and_the_object_model(1)`

You are the specialist for `mode_type_bits` in the 'git internals and the object model' knowledge system. Your CERTIFIED TERRITORY (the relative root — everything your concept bundles from):

  executable_file_mode [deep_tree_object]: Mode 100755; regular file with execute bits set; Git marks it this way to preserve the executable bit across platforms that handle it differently.
  regular_file_mode [deep_tree_object]: Mode 100644; standard blob-backed file with read permission for all and write for owner; the default for non-executable files committed to Git.
  submodule_pointer [git_internals_and_the_object_model]: Entry in a parent repository's tree object referencing a specific commit of a nested repository; stored as mode 160000 with commit SHA-1.
  subtree_mode [deep_tree_object]: Mode 040000; entry points to a nested tree object representing a directory; the tree entry name contains a forward slash but the slash is not stored in the entry itself.
  symlink_mode [deep_tree_object]: Mode 120000; entry points to a blob object containing the target path as raw bytes; the blob content is the symlink destination, not the link data itself.

YOUR JOB: define this territory ONE LEVEL OF GRANULARITY DEEPER than it currently is. Name the parts inside the parts. Every claim you emit is proof-checked; incoherence returns as named residue — repair it exactly. You never invent formats: emit exactly the JSONL construction schema you are given.
