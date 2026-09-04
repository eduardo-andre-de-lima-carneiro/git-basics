# 2.2 Configure Identity and Defaults

Set the name and email that Git records on new commits:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

`user.name` and `user.email` are stored in every commit you make and cannot be changed retroactively without rewriting history, so set them before your first commit. `init.defaultBranch` only affects repositories created afterward with `git init`; it does not rename branches in repositories you already have.

Review the effective configuration, and which file each value came from, with:

```bash
git config --list --show-origin
```

## Configuration scope levels

Git reads configuration from several files and merges them, with a more specific scope overriding a less specific one. From lowest to highest precedence:

| Scope | Flag | Applies to | Typical location |
| --- | --- | --- | --- |
| System | `--system` | Every user on the machine | `/etc/gitconfig` (Linux/macOS); `C:\ProgramData\Git\config` (Windows) |
| Global | `--global` | The current user, all repositories | `~/.gitconfig` or `$XDG_CONFIG_HOME/git/config` (Linux/macOS); `%USERPROFILE%\.gitconfig` (Windows) |
| Local | `--local` (default) | The current repository only | `.git/config` inside the repository |
| Worktree | `--worktree` | One worktree of a repository with multiple worktrees | `.git/config.worktree` (only used when `extensions.worktreeConfig` is enabled) |

Local overrides global, which overrides system; worktree, when enabled, overrides all three. Running `git config` with no scope flag writes to `--local`, so run it from inside a repository only when you mean to set a value for that repository alone. See the [`git-config` reference](https://git-scm.com/docs/git-config#FILES) for the full file-discovery rules, including how `$XDG_CONFIG_HOME` is resolved.

## Editor configuration

Git opens an external editor for commit messages, interactive rebase, and similar tasks, controlled by `core.editor`. This course covers editor and merge-tool setup in detail in [Editor and Merge Tool Configuration](../05-ide-integration/07-editor-and-mergetool-config.md); a minimal example:

```bash
git config --global core.editor "code --wait"
```

## Common pitfalls

- **Forgetting `user.email`.** Without it, Git either refuses to commit or falls back to a guessed address built from your system username and hostname, producing commits attributed to the wrong person — a problem especially on shared or CI machines. Confirm with `git config --get user.email` before your first commit in a new environment.
- **Setting identity only globally on a shared machine.** If multiple people or roles use the same account (for example, a CI runner), set `user.name`/`user.email` with `--local` per repository instead of relying on one global identity.
- **Confusing scope precedence.** A value set with `--local` always wins over the same key set with `--global`, even if the global value was set more recently. Use `git config --list --show-origin` when a setting doesn't seem to take effect.

## Exercise

Run `git config --global user.name "Your Name"`, `git config --global user.email "you@example.com"`, and `git config --global init.defaultBranch main`. Then run `git config --list --show-origin` and confirm all three values appear with your global config file as their origin.

## References

- Git reference manual — [git-config](https://git-scm.com/docs/git-config)
- Pro Git (2nd edition) — [First-Time Git Setup](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)
- Pro Git (2nd edition) — [Git Configuration](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration)
