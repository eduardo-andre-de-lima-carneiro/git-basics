# 3.1 The Daily Workflow

Every change moves through three places before it is safe: the **working tree** (files you edit), the **staging area** or index (what will go into the next commit), and the **repository history** (commits already recorded). Use a small, observable loop to move deliberately between them:

```bash
git status
git add path/to/file
git diff --staged
git commit -m "Describe the change"
git status
```

## What each command actually checks

- [`git status`](https://git-scm.com/docs/git-status) reports three groups: changes staged for commit, changes not staged for commit, and untracked files. Reading which group a file is in tells you exactly what the next `git add` or `git commit` will do to it.
- [`git diff`](https://git-scm.com/docs/git-diff) with no arguments compares the working tree against the index — it shows edits you *could* stage but haven't yet.
- `git diff --staged` (a synonym for `--cached`) compares the index against `HEAD` instead — it shows exactly what the next commit will contain, which is why reviewing it before `git commit` catches mistakes that `git diff` alone would miss.
- [`git add`](https://git-scm.com/docs/git-add) copies file content into the index. It is a snapshot at the moment you run it: edit the file again afterward, and you must run `git add` a second time before those new edits are included.

## Staging part of a file

`git add path/to/file` stages the whole file. When only some of your edits belong in this commit, stage individual hunks instead:

```bash
git add -p path/to/file
```

This walks through each changed hunk and asks whether to stage it, letting you split unrelated edits in the same file across separate, focused commits.

## Common pitfalls

- `git add .` stages everything under the current directory, including files you touched for unrelated reasons (debug prints, local config, stray editor files). Prefer naming paths explicitly, or use `git add -p`, and keep files that should never be staged out of the picture with [`.gitignore`](https://git-scm.com/docs/gitignore).
- Committing without checking `git diff --staged` is the most common way unrelated changes end up in a commit — the staging area can silently hold more than you remember adding.

## Exercise

In a practice repository, edit two unrelated files. Stage only one hunk from one file with `git add -p`, confirm with `git status` and `git diff --staged` that the staging area holds exactly that hunk, commit it, then verify the other edits are still untouched with `git status`.

## References

- Git reference — [git-status](https://git-scm.com/docs/git-status)
- Git reference — [git-diff](https://git-scm.com/docs/git-diff)
- Git reference — [git-add](https://git-scm.com/docs/git-add)
- Git reference — [gitignore](https://git-scm.com/docs/gitignore)
- Pro Git (2nd ed.) — [Recording Changes to the Repository](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository)
