# 3.3 Branches and Collaboration

Branches are movable names pointing to commits. Create work away from the shared base:

```bash
git switch -c feature/example
git switch main
git merge feature/example
```

## What `switch -c` and `merge` actually do

- [`git switch -c <name>`](https://git-scm.com/docs/git-switch) creates the new branch and switches to it as one transactional step — equivalent to `git branch <name>` followed by `git switch <name>`, except the branch is never left half-created if the switch fails.
- [`git merge`](https://git-scm.com/docs/git-merge) behaves differently depending on the history shape:
  - **Fast-forward:** if the current branch's tip is an ancestor of the branch being merged in — no local commits diverged — Git just moves the branch pointer forward. No merge commit is created.
  - **Merge commit:** if both branches have commits the other lacks, Git creates a new commit with two parents to combine them. Pass `--no-ff` to force a merge commit even when a fast-forward is possible, if you want the branch's existence to stay visible in history.

## Conflicts are a decision, not a failure

Before merging, inspect the history and resolve conflicts deliberately. A conflict means the same lines changed on both sides and Git cannot guess which version — or combination — is correct; it is a request for a human decision, not a command failure to hide by blindly accepting one side.

## Common pitfalls

- Long-lived branches accumulate divergence and produce larger, harder-to-resolve conflicts. Merging `main` into a feature branch periodically (or rebasing it, for unpublished work) keeps the eventual merge small.
- `git merge --no-ff` versus a plain fast-forward changes what your history looks like permanently — decide on a convention for the team rather than mixing both inconsistently.

## Exercise

In a practice repository, create a branch, commit once, and merge it back into `main` with no other commits in between — confirm with `git log --oneline --graph` that no merge commit was created (a fast-forward). Then create a second branch, make a commit on `main` too, and merge again — confirm this time a merge commit appears.

## References

- Git reference — [git-switch](https://git-scm.com/docs/git-switch)
- Git reference — [git-branch](https://git-scm.com/docs/git-branch)
- Git reference — [git-merge](https://git-scm.com/docs/git-merge)
- Pro Git (2nd ed.) — [Branches in a Nutshell](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)
