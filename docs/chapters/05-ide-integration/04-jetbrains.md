# 5.4 JetBrains IDEs

IntelliJ IDEA, PyCharm, WebStorm, PhpStorm, Rider, GoLand, and Android Studio share the same [Git integration](https://www.jetbrains.com/help/idea/using-git-integration.html) under the **Git** (or **VCS**) menu.

## Core workflow

- **Git > Clone** creates the local repository; **VCS > Enable Version Control Integration** starts one in an existing project.
- The [**Commit** tool window](https://www.jetbrains.com/help/idea/commit-and-push-changes.html) lists changes, groups them into changelists, and stages files or hunks. A message box and **Commit** / **Commit and Push** buttons sit below it.
- The **Git** tool window's **Log** tab shows the full branch graph with filtering by branch, user, and path.
- The branch widget in the status bar switches, creates, and compares branches.
- **Update Project** runs fetch plus merge or rebase, based on your setting.
- Conflicts open a three-pane resolver with **Accept Left**, **Accept Right**, and manual editing in the result pane.

## Interactive rebase

Right-click a commit in the **Log** and choose **Interactively Rebase from Here** to reorder, squash, edit, or drop commits through a dialog instead of a text file.

## Shelve versus stash

**Shelve** is a JetBrains feature that sets changes aside in the IDE. **Stash** is the Git command. Both work; prefer stash if teammates on other editors need to see the same saved state through Git.

## Exercise

In a practice repository, make two unrelated edits, split them into two changelists in the **Commit** tool window, and commit them separately. Confirm the two commits in the **Log** tab.

## References

- JetBrains — [Git integration in IntelliJ IDEA](https://www.jetbrains.com/help/idea/using-git-integration.html)
- JetBrains — [Commit and push changes](https://www.jetbrains.com/help/idea/commit-and-push-changes.html)
- JetBrains — [Edit Git project history (interactive rebase)](https://www.jetbrains.com/help/idea/edit-project-history.html)
- JetBrains — [Resolve Git conflicts](https://www.jetbrains.com/help/idea/resolve-conflicts.html)
