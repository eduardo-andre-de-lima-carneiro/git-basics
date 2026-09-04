# 3.6 Practical Exercises

Complete these in a temporary directory:

1. Initialize a repository, create a file, and make two focused commits. Between commits, use `git status` and `git diff --staged` to confirm exactly what each commit will contain before running `git commit`.
2. Create a branch, change the same line differently on both branches, and resolve the merge conflict deliberately rather than accepting either side automatically.
3. Add a remote, fetch its history, and compare local and remote branches with `git log --oneline main..origin/main` before integrating anything.
4. Practice restoring an unstaged edit with `git restore`, unstaging a file with `git restore --staged`, and reverting a published commit with `git revert` — using the [3.5 decision table](05-undo.md) to pick the right command for each case.

For each exercise, record the command used, the state before it, and the result shown by `git status`.

## References

- Git reference — [git-status](https://git-scm.com/docs/git-status)
- Git reference — [git-log](https://git-scm.com/docs/git-log)
- Git reference — [git-restore](https://git-scm.com/docs/git-restore)
- Git reference — [git-revert](https://git-scm.com/docs/git-revert)
