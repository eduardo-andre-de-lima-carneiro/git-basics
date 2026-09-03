# 5.7 Editor and Merge Tool Configuration

Git uses three settings to hand work to an external program: `core.editor` for text, `merge.tool` for conflict resolution, and `diff.tool` for viewing changes.

## Set the commit editor

```bash
git config --global core.editor "code --wait"     # VS Code
git config --global core.editor "codium --wait"   # VSCodium
```

For a JetBrains IDE, use its command-line launcher, for example `git config --global core.editor "idea --wait"` once the launcher is installed.

## Configure a merge tool

```bash
git config --global merge.tool vscode
git config --global mergetool.vscode.cmd 'code --wait --merge $REMOTE $LOCAL $BASE $MERGED'
git config --global mergetool.keepBackup false
```

When a conflict happens, run:

```bash
git mergetool
```

Git opens the configured tool for each conflicted file. After you save and close, mark the result with `git add` and continue the merge or rebase.

## Configure a diff tool

```bash
git config --global diff.tool vscode
git config --global difftool.vscode.cmd 'code --wait --diff $LOCAL $REMOTE'
git difftool HEAD~1 HEAD
```

Visual Studio and JetBrains IDEs also register themselves as merge and diff tools during installation on most platforms; check their documentation for the exact `merge.tool` name.

## Exercise

Configure `merge.tool`, create a conflict in a practice repository by editing the same line on two branches, run `git mergetool`, resolve it in the editor, and finish with `git commit`.
