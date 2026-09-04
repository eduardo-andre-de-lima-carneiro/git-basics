# 5.3 Visual Studio

Visual Studio (the full Windows IDE, not VS Code) has [built-in Git support](https://learn.microsoft.com/en-us/visualstudio/version-control/git-with-visual-studio) through the **Git** menu and two docked windows.

## Core workflow

- **Git > Clone Repository** or **Create Git Repository** starts a repository, offering a `.gitignore` and license template.
- The **Git Changes** window shows unstaged and staged changes, the commit message box, and the **Commit** / **Commit and Push** buttons.
- The **Git Repository** window shows the branch graph, incoming and outgoing commits, and lets you fetch, pull, push, merge, rebase, and manage branches.
- The branch selector on the status bar switches and creates branches.
- Merge conflicts open in the **Merge Editor**, with checkboxes for taking incoming, current, or both changes.

## Authentication

Visual Studio uses [**Git Credential Manager**](https://github.com/git-ecosystem/git-credential-manager), installed with it, to store platform tokens in the Windows Credential Store. Sign in through **Git > Settings** or the account picker; avoid putting credentials in remote URLs.

## Note on Team Explorer

Older versions routed Git through **Team Explorer**. Current versions use the dedicated Git menu and windows described above; the newer experience is the one to learn.

## Exercise

In a practice repository opened in Visual Studio, make a change, stage it in **Git Changes**, commit, and then open the **Git Repository** window to confirm the new commit appears in the graph.

## References

- Microsoft Learn — [About Git in Visual Studio](https://learn.microsoft.com/en-us/visualstudio/version-control/git-with-visual-studio)
- Microsoft Learn — [Resolve merge conflicts in Visual Studio](https://learn.microsoft.com/en-us/visualstudio/version-control/git-resolve-conflicts)
- git-ecosystem — [Git Credential Manager](https://github.com/git-ecosystem/git-credential-manager)
