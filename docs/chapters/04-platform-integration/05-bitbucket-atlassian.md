# 4.5 Bitbucket and Atlassian

Bitbucket, from Atlassian, provides Git repositories with pull requests and Pipelines. It can connect repository work to Jira issues and other Atlassian services.

## Connect and publish

Create a Bitbucket Cloud repository, then run locally:

```bash
git remote add origin https://bitbucket.org/WORKSPACE/REPOSITORY.git
git push -u origin main
```

Use the clone URL provided by your Bitbucket workspace. Bitbucket Data Center uses organization-specific URLs and authentication policies.

## Useful integrations

- Pull requests provide review, approvals, tasks, and merge checks.
- `bitbucket-pipelines.yml` defines Bitbucket Pipelines build and deployment steps.
- Jira integration links branches, commits, and pull requests to work items.
- Deployment environments can restrict variables and production releases.
- Marketplace and webhooks connect Bitbucket to additional engineering tools.

Use repository or workspace access tokens with the smallest required permissions. Keep Jira issue keys in branch names or commit messages only when that convention is adopted by the team, and never place secrets in those fields.
