# 4.2 GitHub

GitHub combines hosted Git repositories with pull requests, Issues, Actions, Projects, Packages, and security features.

## Connect and publish

Create an empty repository on GitHub, then run locally:

```bash
git remote add origin https://github.com/OWNER/REPOSITORY.git
git push -u origin main
```

Replace `OWNER`, `REPOSITORY`, and `main` with your values. Do not initialize the GitHub repository with a second README when your local repository already has one, unless you plan to reconcile the histories.

## Useful integrations

- Pull requests provide review, discussion, required approvals, and status checks.
- GitHub Actions can test, scan, package, and deploy on pushes or pull requests.
- Branch protection can require reviews, passing checks, and signed commits.
- Environments can restrict deployments and protect production secrets.
- Webhooks and the API connect repository events to external systems.

Use least-privilege fine-grained personal access tokens or GitHub Apps. Store automation secrets in repository or environment secrets, never in workflow files or source code.
