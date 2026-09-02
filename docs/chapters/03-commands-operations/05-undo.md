# 3.5 Undoing Changes Safely

Choose the command based on where the unwanted change exists:

- Working tree: `git restore <file>`. This permanently discards the file's uncommitted working-tree changes, so back up anything you may need first.
- Staging area: `git restore --staged <file>`.
- Published history: prefer `git revert <commit>`.
- Unpublished local commit: consider `git reset` only after checking the consequences.

Run `git status` before and after recovery commands.
