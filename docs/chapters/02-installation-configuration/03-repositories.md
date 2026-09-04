# 2.3 Local and Remote Repositories

## `git init` vs. `git clone`

Start a brand-new project locally with [`git init`](https://git-scm.com/docs/git-init):

```bash
git init
```

This creates a `.git` subdirectory in the current folder and turns it into a Git repository with no commits and no remote configured. Copy an existing project — history included — with [`git clone`](https://git-scm.com/docs/git-clone):

```bash
git clone <repository-url>
```

`git clone` creates a new directory, copies the entire history, checks out the default branch, and automatically configures a remote named `origin` pointing back at the source. Use `git init` when a project doesn't exist as a Git repository yet; use `git clone` when one already does, whether on a hosting platform or on a local path.

## What `.git/` actually contains

Both commands leave you with a `.git/` directory holding the repository's real data — the working files you see are just a checked-out snapshot of it. It includes:

- `objects/` — the content-addressed store of commits, trees, and blobs (the actual history).
- `refs/heads/` and `refs/tags/` — pointers to branch tips and tags.
- `HEAD` — which branch (or commit) is currently checked out.
- `config` — the repository's local configuration (`--local` scope, see [2.2](02-configure.md)).
- After a clone, `refs/remotes/origin/` plus `remote.origin.url` and `remote.origin.fetch` in `config`, recording where the repository was cloned from.

Deleting `.git/` deletes the repository's entire history; the working files that remain are no longer tracked by Git.

## HTTPS vs. SSH remote URLs

A remote URL takes one of two common forms:

```bash
# HTTPS
https://github.com/OWNER/REPOSITORY.git

# SSH
git@github.com:OWNER/REPOSITORY.git
```

HTTPS works from any network without extra local setup and authenticates with a personal access token instead of your account password; it's the simpler starting point. SSH authenticates with a key pair registered on the platform and is more convenient for frequent pushes once configured, since it doesn't prompt for a token each time. Either form works with both `git clone` and `git remote add`. Platform-specific setup for tokens and SSH keys is covered in [Chapter 4: Platform Integration](../04-platform-integration/01-integration-fundamentals.md#choose-https-or-ssh); pick whichever form matches how you've already authenticated with the platform.

## Inspect and manage remotes

```bash
git remote -v
```

Lists every configured remote and its URL for fetch and push. A freshly cloned repository shows `origin`; add another with `git remote add <name> <url>`, or change an existing one with `git remote set-url <name> <url>` (for example, switching `origin` from HTTPS to SSH without re-cloning).

## Common pitfalls

- **Running `git clone` into a directory that already exists.** Git refuses to clone into a non-empty directory, so `git clone <url>` inside an existing project folder fails; either clone into a new directory or pass a target directory name as the second argument.
- **Running `git init` inside an already-cloned repository.** This reinitializes `.git/` in place — normally harmless (existing history and config are preserved) — but it's rarely what you meant to do; check `git status` or look for an existing `.git/` first if you're unsure whether a folder is already a repository.
- **Assuming a clone always tracks `origin`.** `origin` is only the conventional name Git assigns automatically; a repository can have zero, one, or several remotes under any names.

## Exercise

Create an empty directory, run `git init` inside it, then run `git remote -v` and confirm it prints nothing (no remote configured yet). In a separate directory, clone any public repository over HTTPS, then run `git remote -v` again and confirm `origin` now appears with both a fetch and a push URL.

## References

- Git reference manual — [git-init](https://git-scm.com/docs/git-init)
- Git reference manual — [git-clone](https://git-scm.com/docs/git-clone)
- Pro Git (2nd edition) — [Getting a Git Repository](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository)
