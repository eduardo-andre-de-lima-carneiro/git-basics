# 5.5 Other Editors

The same Git concepts appear in many other tools. This is a short orientation, not a full guide for each.

- [**Xcode**](https://developer.apple.com/documentation/xcode/source-control-management) has a **Source Control** menu and navigator for commit, push, pull, branch, and conflict resolution on macOS projects.
- **Eclipse** uses the [**EGit**](https://wiki.eclipse.org/EGit/User_Guide) plugin, which adds a **Git Staging** view and a **History** view.
- [**Sublime Merge**](https://www.sublimemerge.com/docs/) is a standalone Git client from the Sublime Text makers, with a fast commit graph and hunk staging; Sublime Text integrates with it.
- **Vim and Neovim** commonly use [`vim-fugitive`](https://github.com/tpope/vim-fugitive) for commands and [`gitsigns.nvim`](https://github.com/lewis6991/gitsigns.nvim) (Neovim) or `vim-gitgutter` for gutter marks.
- **Emacs** users rely on [**Magit**](https://magit.vc/), a keyboard-driven interface that mirrors most Git commands.
- [**GitHub Desktop**](https://docs.github.com/en/desktop) and **GitKraken** are graphical clients that pair well with any editor.

Whatever the tool, it is calling Git. If a panel and `git status` disagree, refresh the panel or trust the command line.

## Exercise

Pick one tool from this list that you do not normally use. Open a practice repository in it, make a commit, and verify the result with `git log --oneline` in a terminal.

## References

- Apple Developer — [Source control management in Xcode](https://developer.apple.com/documentation/xcode/source-control-management)
- Eclipse — [EGit User Guide](https://wiki.eclipse.org/EGit/User_Guide)
- [Sublime Merge documentation](https://www.sublimemerge.com/docs/)
- GitHub — [tpope/vim-fugitive](https://github.com/tpope/vim-fugitive)
- GitHub — [lewis6991/gitsigns.nvim](https://github.com/lewis6991/gitsigns.nvim)
- [Magit — a Git porcelain inside Emacs](https://magit.vc/)
- GitHub Docs — [GitHub Desktop](https://docs.github.com/en/desktop)
