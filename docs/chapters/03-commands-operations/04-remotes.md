# 3.4 Remotes and Synchronization

Synchronize explicitly:

```bash
git fetch origin
git log --oneline main..origin/main
git push -u origin feature/example
```

Fetch first when you need to understand what changed remotely. Push only commits you have reviewed.
