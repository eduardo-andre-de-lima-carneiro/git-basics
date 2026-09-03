# 5.1 IDE Integration Fundamentals

An editor's Git integration is a view over the same repository the command line uses. It reads `git status`, `git diff`, and `git log` for you and turns common actions into buttons, gutters, and panels.

## What the integration adds

- A source control panel that lists changed, staged, and untracked files.
- Inline gutter marks that show added, changed, and removed lines.
- A visual diff for a file or a single block of lines (a "hunk").
- A commit box for the message, with staging done by clicking files or hunks.
- A branch indicator in the status bar for switching and creating branches.
- A three-pane view for resolving merge conflicts.

## When to still use the terminal

Reach for the command line when you need exact control or an uncommon operation: interactive rebase details, `git reflog`, `git bisect`, custom `git log` filters, or scripting. The editor and the terminal act on the same `.git` directory, so you can move between them freely.

## Shared setup

- Configure identity once with `git config --global user.name` and `user.email` (see [2.2 Configure identity and defaults](../02-installation-configuration/02-configure.md)).
- Let a credential helper or the OS keychain store tokens so the editor does not prompt on every push.
- Decide whether editor-specific folders such as `.vscode/` or `.idea/` belong in the repository; if not, add them to `.gitignore`.
- Keep signing (SSH or GPG) configured in Git itself so commits made from the editor are signed too.

## Exercise

Open an existing practice repository in your editor. Change one line in a file, then confirm the editor's source control panel and `git status` in a terminal report the same change.
