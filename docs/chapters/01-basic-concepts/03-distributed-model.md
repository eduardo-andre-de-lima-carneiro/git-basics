# 1.3 Git's Distributed Model

An individual repository normally has a working tree, a local history, and optional remote repositories. A remote is a collaboration endpoint, not the definition of Git itself. See the Pro Git book's [overview of version control](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control) for how this differs from a centralized VCS.

## Common operations

Common operations have distinct purposes:

- [`clone`](https://git-scm.com/docs/git-clone) copies a repository, including its full history.
- [`fetch`](https://git-scm.com/docs/git-fetch) downloads remote history without changing local work — it only updates the remote-tracking branches (e.g. `origin/main`).
- [`pull`](https://git-scm.com/docs/git-pull) runs `fetch` and then integrates the result into the current branch (merge or rebase, depending on configuration).
- [`push`](https://git-scm.com/docs/git-push) publishes local commits to a remote.

## Common pitfalls

- **"Distributed" does not mean "no central server in practice."** Git itself has no required central repository — any clone can act as a remote for any other — but most teams still designate one remote (often hosted on GitHub, GitLab, or similar) as the shared source of truth by convention, not because Git technically requires it.
- **`fetch` is safe, `pull` can surprise you.** Because `pull` also merges or rebases, run [`git fetch`](https://git-scm.com/docs/git-fetch) first if you want to inspect incoming changes before they touch your working branch.
- **A remote name is just a label.** [`git remote`](https://git-scm.com/docs/git-remote) shows the short names (like `origin`) mapped to actual URLs; the name has no special meaning to Git beyond that mapping.

## Exercise

Run `git remote -v` in an existing clone to see the URLs behind its remote names. Then run `git fetch` and compare `git log main` with `git log origin/main` — the difference is exactly what `pull` would bring in.

## References

- Pro Git (2nd ed.) — [About Version Control](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)
- Git reference — [git-clone](https://git-scm.com/docs/git-clone)
- Git reference — [git-fetch](https://git-scm.com/docs/git-fetch)
- Git reference — [git-pull](https://git-scm.com/docs/git-pull)
- Git reference — [git-push](https://git-scm.com/docs/git-push)
- Git reference — [git-remote](https://git-scm.com/docs/git-remote)
