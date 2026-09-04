# 1.4 Git's Mental Model

Think in three places:

1. Working tree: files currently being edited.
2. Staging area: the next snapshot being prepared.
3. Repository history: committed snapshots.

The basic flow is `edit -> git add -> git commit`. `git status` shows the differences between these places and should be your most frequent diagnostic command.

## Why staging is a separate step

The staging area (also called the index) lets you build a commit out of only part of your changes — for example, stage one finished fix with `git add` while leaving an unrelated, still-in-progress edit in the working tree unstaged. What ends up in the commit is exactly what was staged at the moment you ran `git commit`, not whatever the file looks like afterward. See [Recording Changes to the Repository](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository) in the Pro Git book.

## Common pitfalls

- **A commit is not a diff.** Each commit points to a full snapshot of the project tree, not a delta from the previous commit; Git computes diffs on demand by comparing two snapshots. This is why checking out an old commit is a direct file-tree swap rather than replaying a chain of patches. See [What is Git?](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F).
- **Staged and modified are not the same state.** If you edit a file again after `git add`, `git status` will show it as both staged and modified — the staged copy is frozen at the moment you ran `add`, and a second `git add` is needed to update it.

## Practice

Change a file, run `git add`, then change the same file again without re-staging. Run `git status`, then `git diff` (working tree vs. staged) and `git diff --staged` (staged vs. last commit), to see the three places disagree.

## References

- Pro Git (2nd ed.) — [Recording Changes to the Repository](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)
- Pro Git (2nd ed.) — [What is Git?](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F)
- Git reference — [git-status](https://git-scm.com/docs/git-status)
- Git reference — [git-diff](https://git-scm.com/docs/git-diff)
