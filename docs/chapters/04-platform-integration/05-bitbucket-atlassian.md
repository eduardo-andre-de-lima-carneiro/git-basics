# 4.5 Bitbucket and Atlassian

Bitbucket, from Atlassian, provides Git repositories with pull requests and Pipelines. It can connect repository work to Jira issues and other Atlassian services.

## Connect and publish

Create a Bitbucket Cloud repository, then run locally:

```bash
git remote add origin https://bitbucket.org/WORKSPACE/REPOSITORY.git
git push -u origin main
```

Use the clone URL provided by your Bitbucket workspace. Bitbucket Data Center uses organization-specific URLs and authentication policies.

## Authentication

Bitbucket Cloud's HTTPS authentication changed in 2026: [app passwords](https://support.atlassian.com/bitbucket-cloud/docs/app-passwords/) were retired on a phased schedule that ended in July 2026 and no longer work at all. The current method for scripts, CI tools, and the Git command line is an [API token](https://support.atlassian.com/bitbucket-cloud/docs/using-api-tokens/), created from your Atlassian account and used together with your Bitbucket username as the Git credential. If a page, tutorial, or tool still tells you to create an "app password," treat that instruction as outdated.

An SSH key ([Ed25519 recommended](https://support.atlassian.com/bitbucket-cloud/docs/set-up-personal-ssh-keys-on-linux/)) is unaffected by the app-password retirement and remains a good option for frequent command-line work.

Enable [two-step verification](https://support.atlassian.com/bitbucket-cloud/docs/enable-two-step-verification/) on the account — via an authenticator app or a security key — independently of which Git credential you use day to day.

## Useful integrations

- Pull requests provide review, approvals, tasks, and merge checks.
- `bitbucket-pipelines.yml` defines Bitbucket Pipelines build and deployment steps.
- Jira integration links branches, commits, and pull requests to work items.
- Deployment environments can restrict variables and production releases.
- [Branch permissions](https://support.atlassian.com/bitbucket-cloud/docs/use-branch-permissions/) restrict who can push or merge to a given branch; Marketplace apps and webhooks connect Bitbucket to additional engineering tools.

Use repository or workspace access tokens with the smallest required permissions. Keep Jira issue keys in branch names or commit messages only when that convention is adopted by the team, and never place secrets in those fields.

## Common pitfalls

- Following an older tutorial that says to create an "app password" — as of mid-2026 that flow no longer exists; create an API token instead.
- An integration (CI tool, package manager, Git client) still configured with a saved app password silently breaking once the retirement schedule reached full removal, with no local warning beforehand.
- Assuming an API token behaves exactly like the old app password: it authenticates Git and API calls, but it cannot be used to sign in to bitbucket.org itself.

## Exercise

Create a Bitbucket API token, then use it together with your Bitbucket username to authenticate a `git push` over HTTPS. Confirm in your account's security settings that no app password is still listed as active.

## References

- Atlassian Support — [App passwords](https://support.atlassian.com/bitbucket-cloud/docs/app-passwords/)
- Atlassian Support — [Using API tokens](https://support.atlassian.com/bitbucket-cloud/docs/using-api-tokens/)
- Atlassian Support — [Enable two-step verification](https://support.atlassian.com/bitbucket-cloud/docs/enable-two-step-verification/)
- Atlassian Support — [Set up personal SSH keys](https://support.atlassian.com/bitbucket-cloud/docs/set-up-personal-ssh-keys-on-linux/)
- Atlassian Support — [Use branch permissions](https://support.atlassian.com/bitbucket-cloud/docs/use-branch-permissions/)
