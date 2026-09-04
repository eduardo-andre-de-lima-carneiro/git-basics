# 4.1 Integration Fundamentals

Hosted platforms add collaboration and delivery services around a Git repository. The local commands remain familiar; the platform supplies identity, permissions, review, automation, and project visibility.

## The common flow

1. Create or select a remote repository.
2. Connect the local repository with [`git remote add origin <repository-url>`](https://git-scm.com/docs/git-remote).
3. Push a branch with `git push -u origin <branch-name>`.
4. Open a pull request or merge request for review.
5. Let required checks run before merging.
6. Delete the short-lived branch after the change is integrated.

## Choose HTTPS or SSH

HTTPS is simple to start with. Every major platform now authenticates HTTPS Git operations with a token or a federated sign-in rather than an account password — GitHub removed password authentication for Git in August 2021, and the other platforms in this chapter have followed the same pattern, each with its own current mechanism (see the platform pages that follow). SSH uses a key pair, avoids re-entering credentials on every operation, and can also sign commits. Never put tokens, private keys, or credentials in a repository, and don't assume a page you read a while ago still describes today's default — these platforms change their authentication defaults more often than most Git commands change.

## Platform comparison

The table reflects each platform's own documentation, checked live rather than recalled from memory. Numeric limits (seats, storage, CI minutes) change often and are intentionally left out — check each platform's current pricing page for those.

| Platform | Hosting model | Default authentication for Git over HTTPS | Review unit's name | Private repositories on the free tier |
| --- | --- | --- | --- | --- |
| [GitHub](https://docs.github.com/en) | SaaS (GitHub.com) or self-hosted (GitHub Enterprise Server) | Personal access token, SSH key, or a credential helper such as GitHub CLI / Git Credential Manager — account passwords are rejected | Pull request | Yes |
| [GitLab](https://docs.gitlab.com/) | SaaS (GitLab.com) or self-hosted (GitLab Self-Managed) | Personal access token (mandatory once 2FA or SSO is enabled) or SSH key | Merge request | Yes |
| [Azure Repos](https://learn.microsoft.com/en-us/azure/devops/repos/) | SaaS (Azure DevOps Services) or self-hosted (Azure DevOps Server) | Microsoft Entra ID sign-in through Git Credential Manager, preferred over a scoped personal access token | Pull request | Yes |
| [Bitbucket](https://support.atlassian.com/bitbucket-cloud/) | SaaS (Bitbucket Cloud) or self-hosted (Bitbucket Data Center) | API token or SSH key — app passwords were fully retired in 2026 | Pull request | Yes |

## What to configure

At minimum, agree on the default branch, branch protection rules, review requirements, status checks, issue linking, and who can push or merge. These policies are part of the team's delivery process, not merely platform decoration.

## Common pitfalls

- Reusing one long-lived, broadly scoped token across every tool. If it leaks, every integration that used it is compromised at once — scope tokens to one purpose each.
- Forgetting that a token has an expiration date. A push that worked yesterday can fail today with an authentication error the moment a token lapses — treat that as routine, not a bug, and rotate the token.
- Assuming HTTPS still asks for an account password. None of the four platforms in this chapter do; the prompt is for a token or a CLI-managed sign-in instead.

## References

- Git reference manual — [git-remote](https://git-scm.com/docs/git-remote)
- GitHub Docs — [About authentication to GitHub](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/about-authentication-to-github)
- GitLab Docs — [Personal access tokens](https://docs.gitlab.com/user/profile/personal_access_tokens/)
- Microsoft Learn — [Use personal access tokens to authenticate](https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate)
- Atlassian Support — [App passwords (Bitbucket Cloud)](https://support.atlassian.com/bitbucket-cloud/docs/app-passwords/)
