# 3.5 Undoing Changes Safely

Git has three different "undo" commands, and they operate on three different places. Picking the right one depends on where the unwanted change lives and whether anyone else has already seen it.

## Decision table: restore vs. revert vs. reset

| Command | Operates on | Rewrites published history? | Typical use | Safety / recovery |
| --- | --- | --- | --- | --- |
| [`git restore <file>`](https://git-scm.com/docs/git-restore) | Working tree (default target) | No — not a history operation | Discard unwanted, uncommitted edits to a file | The discarded content is gone; Git keeps no reflog of working-tree edits, so back up anything you might need first |
| `git restore --staged <file>` | Staging area (index) only | No | Unstage a file added by mistake, keeping its edits in the working tree | Safe — the working tree is untouched, nothing is lost |
| [`git revert <commit>`](https://git-scm.com/docs/git-revert) | History, by adding a new commit | No — it records a new commit that reverses the change instead of altering existing commits | Undo the effect of a commit that has already been pushed or shared | Safe on shared branches; may need conflict resolution if later commits touched the same lines |
| [`git reset [--soft\|--mixed\|--hard] <commit>`](https://git-scm.com/docs/git-reset) | `HEAD` and the index; `--hard` also overwrites the working tree | Yes — moves the branch pointer, dropping commits from that branch's history | Undo local, unpublished commits, or unstage everything at once | Never use on commits someone else already has; dropped commits usually stay recoverable for a while via [`git reflog`](https://git-scm.com/docs/git-reflog), but `--hard` also discards uncommitted working-tree edits, which reflog cannot bring back |

The three `reset` modes differ in how far back they undo: `--soft` moves only `HEAD` (index and working tree untouched — useful for squashing recent commits before recommitting), `--mixed` (the default) also resets the index so nothing is staged, and `--hard` additionally overwrites the working tree to match the target commit.

## Why this order of preference matters

Prefer `restore` and `revert` by default because neither can alter history other people rely on. Reach for `reset` only when you are certain the commits in question are still private — the official documentation is explicit: do not reset away commits you have already given to somebody else, because their local history will silently diverge from yours.

## Common pitfalls

- Confusing `git restore <file>` (working tree) with `git restore --staged <file>` (index) is the most common mistake — the flag changes which layer is affected, not just how much is undone.
- `git reset --hard` is the one command in this table that can destroy uncommitted work with no recovery path. Run `git status` immediately before it.
- Run `git status` before and after any recovery command — it is the cheapest way to confirm you changed the layer you meant to.

## Exercise

In a practice repository: (1) edit a file without staging it, then discard the edit with `git restore`; (2) stage a file, then unstage it with `git restore --staged` and confirm the edit is still present; (3) commit a change, then undo its effect with `git revert` and confirm two commits now exist; (4) make one more commit, undo it locally with `git reset --mixed HEAD~1`, confirm with `git status` that the change is now unstaged, then find the dropped commit again with `git reflog`.

## References

- Git reference — [git-restore](https://git-scm.com/docs/git-restore)
- Git reference — [git-revert](https://git-scm.com/docs/git-revert)
- Git reference — [git-reset](https://git-scm.com/docs/git-reset)
- Git reference — [git-reflog](https://git-scm.com/docs/git-reflog)
- Pro Git (2nd ed.) — [Reset Demystified](https://git-scm.com/book/en/v2/Git-Tools-Reset-Demystified)
