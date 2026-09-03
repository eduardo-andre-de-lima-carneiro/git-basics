# 5.5 Other Editors

The same Git concepts appear in many other tools. This is a short orientation, not a full guide for each.

- **Xcode** has a **Source Control** menu and navigator for commit, push, pull, branch, and conflict resolution on macOS projects.
- **Eclipse** uses the **EGit** plugin, which adds a **Git Staging** view and a **History** view.
- **Sublime Merge** is a standalone Git client from the Sublime Text makers, with a fast commit graph and hunk staging; Sublime Text integrates with it.
- **Vim and Neovim** commonly use `vim-fugitive` for commands and `gitsigns` (Neovim) or `vim-gitgutter` for gutter marks.
- **Emacs** users rely on **Magit**, a keyboard-driven interface that mirrors most Git commands.
- **GitHub Desktop** and **GitKraken** are graphical clients that pair well with any editor.

Whatever the tool, it is calling Git. If a panel and `git status` disagree, refresh the panel or trust the command line.

## Exercise

Pick one tool from this list that you do not normally use. Open a practice repository in it, make a commit, and verify the result with `git log --oneline` in a terminal.
