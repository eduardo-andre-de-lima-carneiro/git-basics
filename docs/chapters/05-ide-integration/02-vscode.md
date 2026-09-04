# 5.2 Visual Studio Code

Visual Studio Code ships with [Git source control support](https://code.visualstudio.com/docs/sourcecontrol/overview) enabled when Git is installed and on the `PATH`.

## Core workflow

- The **Source Control** view (Ctrl/Cmd+Shift+G) lists changes. Hover a file and click **+** to stage it, or stage a single block from the diff editor.
- Type a message in the commit box and press Ctrl/Cmd+Enter to commit.
- The branch name in the bottom-left status bar opens the branch switch and create menu.
- **Sync Changes** runs `git pull` then `git push` for the current branch.
- The **Timeline** view at the bottom of the Explorer shows a file's commit history.

## Use VS Code as Git's editor

```bash
git config --global core.editor "code --wait"
```

The `--wait` flag makes Git pause until you close the tab, which is required for commit messages and interactive rebase.

## Helpful extensions

- [**GitLens**](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) adds line-by-line blame, a commits graph, and history navigation.
- [**GitHub Pull Requests and Issues**](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github) lets you create, review, and merge pull requests without leaving the editor.

Install extensions only from publishers you trust, and review the permissions they request.

## Exercise

Set `core.editor` to `code --wait`, then run `git commit` with no `-m` in a practice repository. Write the message in the VS Code tab, save, and close it; confirm the commit was recorded with `git log --oneline`.

## References

- Visual Studio Code — [Using Git source control in VS Code](https://code.visualstudio.com/docs/sourcecontrol/overview)
- Visual Studio Marketplace — [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens)
- Visual Studio Marketplace — [GitHub Pull Requests and Issues](https://marketplace.visualstudio.com/items?itemName=GitHub.vscode-pull-request-github)
- Git reference — [git-config](https://git-scm.com/docs/git-config)
