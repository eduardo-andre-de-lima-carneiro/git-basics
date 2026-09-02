# 3.3 Branches and Collaboration

Branches are movable names pointing to commits. Create work away from the shared base:

```bash
git switch -c feature/example
git switch main
git merge feature/example
```

Before merging, inspect the history and resolve conflicts deliberately. A conflict is a request for a human decision, not a command failure to hide.
