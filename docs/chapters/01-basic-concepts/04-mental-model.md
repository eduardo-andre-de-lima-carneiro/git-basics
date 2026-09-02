# 1.4 Git's Mental Model

Think in three places:

1. Working tree: files currently being edited.
2. Staging area: the next snapshot being prepared.
3. Repository history: committed snapshots.

The basic flow is `edit -> git add -> git commit`. `git status` shows the differences between these places and should be your most frequent diagnostic command.
