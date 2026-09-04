# 3.4 Remotes and Synchronization

Synchronize explicitly:

```bash
git fetch origin
git log --oneline main..origin/main
git push -u origin feature/example
```

## Fetch, pull, and push are not the same operation

- [`git fetch`](https://git-scm.com/docs/git-fetch) downloads commits and updates your remote-tracking refs (`origin/main`, for example) but never touches your working tree or local branches. It is always safe to run.
- `git log --oneline main..origin/main` then shows exactly which commits exist on `origin/main` but not yet on your local `main` — a review step before you integrate anything.
- [`git pull`](https://git-scm.com/docs/git-pull) runs `git fetch` and then integrates the result into your current branch. **Its default integration mode is `--ff-only`**: if your local branch has diverged from the remote (both sides have new commits), plain `git pull` fails rather than silently creating a merge commit. Pass `--rebase` to replay your local commits on top of the fetched history instead of merging, or `--no-rebase` to allow a merge commit.
- [`git push -u origin <branch>`](https://git-scm.com/docs/git-push) pushes the branch and records the upstream tracking relationship (`branch.<name>.remote` / `branch.<name>.merge`) in one step. After that, plain `git push` and `git pull` on this branch know which remote branch to use without naming it again.

## Common pitfalls

- `git pull --rebase` rewrites the commits it replays. That is safe for commits only you have — it is unsafe once someone else has fetched them, because their history and yours will no longer match. Reserve `--rebase` for branches you have not shared, and prefer a merge (or `git pull --no-rebase`) once others depend on your commits.
- Because `git pull`'s default is now fail-on-divergence rather than merge-on-divergence, don't assume an old tutorial's description of "pull always merges" still matches your Git version — check `pull.rebase` and `pull.ff` in `git config --list` if behavior seems inconsistent across machines.
- Fetch before you push when working on a shared branch; pushing without first checking `main..origin/main` risks a rejected push or an avoidable conflict.

## Exercise

In a practice repository with a remote configured, run `git fetch origin`, then `git log --oneline main..origin/main` to see what changed remotely before touching anything locally. Push a new branch with `git push -u origin <branch>`, then confirm the tracking relationship with `git branch -vv`.

## References

- Git reference — [git-fetch](https://git-scm.com/docs/git-fetch)
- Git reference — [git-pull](https://git-scm.com/docs/git-pull)
- Git reference — [git-push](https://git-scm.com/docs/git-push)
- Pro Git (2nd ed.) — [Working with Remotes](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes)
