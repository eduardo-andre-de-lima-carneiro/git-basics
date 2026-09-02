# 3.1 The Daily Workflow

Use a small, observable loop:

```bash
git status
git add path/to/file
git diff --staged
git commit -m "Describe the change"
git status
```

Review the staged diff before committing. This habit prevents unrelated files from entering a commit.
