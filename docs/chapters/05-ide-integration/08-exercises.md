# 5.8 Practical Exercises

Complete these in a temporary repository, using your editor for the Git actions and a terminal to verify.

1. Stage a single hunk (not the whole file) from the editor's diff view, commit it, and confirm with `git show`.
2. Create and switch to a branch from the status bar, make a commit, and switch back.
3. Configure your editor as `core.editor`, then run `git commit` with no `-m` and write the message in the editor.
4. Create a merge conflict on one line, resolve it with the editor's three-pane merge view, and finish the merge.
5. Configure `merge.tool` and repeat exercise 4 using `git mergetool` instead of the built-in panel.
6. Make a signed commit from the editor and verify it with `git log --show-signature`.

For each exercise, record the editor action taken and the command output that confirmed the result.
