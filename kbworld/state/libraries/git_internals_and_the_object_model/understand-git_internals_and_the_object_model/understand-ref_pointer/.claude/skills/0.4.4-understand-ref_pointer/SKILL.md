---
name: 0.4.4-understand-ref_pointer
description: [0.4.4] Named file under .git/refs/ containing a SHA-1; represents a branch tip, tag, or remote-tracking branch; updat
---

# understand-ref_pointer

**CALL NUMBER:** `git_internals_and_the_object_model.ref_pointer`
**DEFINITION:** Named file under .git/refs/ containing a SHA-1; represents a branch tip, tag, or remote-tracking branch; updated atomically during operations.

Invoke this skill to understand `ref_pointer` down to its primitives. The RELATIVE ROOT below is the least-fixed-point closure of everything it bundles from — the full import cone, grouped by the lib each prim comes from. Projected from a prover-typed KB (MAP/SWI-Prolog consistency gate): every reference below resolves.

## THE RELATIVE ROOT (the import cone, by lib)

### from `git_internals_and_the_object_model`
- **heads_namespace** (d1): Namespace .git/refs/heads/ containing local branch references; each file = branch name; its SHA-1 = tip commit.
- **packed_refs** (d1): Consolidated .git/packed-refs file containing refs not in loose format; created by git pack-refs; enables faster startup on repos with many refs.
- **ref_transaction** (d1): Atomic multi-ref update mechanism; all-or-nothing semantics; used by git update-ref --transaction for safe concurrent modifications.
- **reflog** (d1): Append-only log at .git/logs/ tracking all ref changes with old SHA, new SHA, timestamp, and actor; enables recovery from accidental resets or branch deletions.
- **remotes_namespace** (d1): Namespace .git/refs/remotes/ containing remote-tracking branches; updated by fetch, not by user edits; represent server state.
- **replace_ref** (d1): Reference under refs/replace/ mapping an object SHA to a substitute SHA; transparent to most commands; allows history rewriting without modifying history.
- **stash_ref** (d1): Pseudo-branch at refs/stash maintained by git stash; each stash entry is a commit whose tree captures working-directory state.
- **tags_namespace** (d1): Namespace .git/refs/tags/ containing tag references; may point directly at commits (lightweight) or at tag objects (annotated).
- **branch_tracking_assignment** (d2): Remote-tracking ref establishing upstream relationship; configured via branch.<name>.remote and branch.<name>.merge; used for push.default and @{upstream}.
- **bisect_log** (d2): refs/bisect/* pseudo-refs tracking midpoints and test results during git bisect; --no-checkout mode walks history without checkout.

## CONSUMERS (what needs this)
`tag_object`

---
*Projected from the `git internals and the object model` KB (162 concepts / 159 relations) — consistency-typed by MAP; the facet list after the colon IS the cross-lib dependency web.*

_(leaf — this is an actual skill.)_
