# 1.3 Git's Distributed Model

An individual repository normally has a working tree, a local history, and optional remote repositories. A remote is a collaboration endpoint, not the definition of Git itself.

Common operations have distinct purposes:

- `clone` copies a repository.
- `fetch` downloads remote history without changing local work.
- `pull` fetches and integrates remote changes.
- `push` publishes local commits.
