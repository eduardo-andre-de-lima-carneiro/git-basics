# 4.3 GitLab

GitLab provides Git repositories with merge requests, Issues, CI/CD pipelines, Package Registry, and security dashboards in one platform.

## Connect and publish

Create a project on GitLab, then run locally:

```bash
git remote add origin https://gitlab.com/GROUP/PROJECT.git
git push -u origin main
```

Use your actual group, project, and default branch names. Review the remote with `git remote -v` before pushing.

## Useful integrations

- Merge requests combine review, approvals, discussions, and pipeline results.
- `.gitlab-ci.yml` defines CI/CD jobs, stages, artifacts, and deployment rules.
- Protected branches and environments control who can merge or deploy.
- Deploy tokens, project access tokens, and runners support automation.
- Webhooks and integrations notify issue trackers, chat tools, and security systems.

Use masked and protected CI/CD variables for credentials. Keep runners patched, restrict privileged runners, and give tokens only the scopes required by their job.
