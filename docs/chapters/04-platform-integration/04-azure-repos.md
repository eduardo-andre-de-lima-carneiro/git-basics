# 4.4 Azure Repos

Azure Repos hosts Git repositories inside Azure DevOps projects and connects naturally to Azure Boards, Pipelines, Test Plans, and Artifacts.

## Connect and publish

Create or select a repository in an Azure DevOps project, then run locally:

```bash
git remote add origin https://dev.azure.com/ORGANIZATION/PROJECT/_git/REPOSITORY
git push -u origin main
```

The exact URL can be copied from the repository's Clone action.

## Authentication

Microsoft's own guidance now puts personal access tokens last, not first: the [Azure DevOps documentation](https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate) says to "avoid using PATs when a more secure authentication method is available" and recommends Microsoft Entra ID sign-in (through Git Credential Manager) or a service principal / managed identity for anything automated. If a [personal access token](https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate) is still the right fit — a one-off script, a tool that can't do an Entra sign-in — give it the narrowest scope and the shortest expiration the task allows; Microsoft's own recommended rotation cadence is 90 days for a personal PAT and 30 days for a privileged one.

[SSH](https://learn.microsoft.com/en-us/azure/devops/repos/git/use-ssh-keys-to-authenticate) is also supported, with one platform-specific catch: Azure Repos accepts only **RSA** keys, not the Ed25519 keys that GitHub and GitLab now recommend — reusing an existing GitHub/GitLab Ed25519 key here fails. Generate a separate RSA key for Azure Repos: `ssh-keygen -t rsa -b 3072`.

## Useful integrations

- Pull requests support reviewers, [branch policies](https://learn.microsoft.com/en-us/azure/devops/repos/git/branch-policies?view=azure-devops), linked work items, and build validation.
- Azure Pipelines can build, test, scan, and deploy from repository events.
- Azure Boards links commits and pull requests to work items for traceability.
- Branch policies can require reviewers, successful builds, and comment resolution — unlike GitHub or GitLab, Azure Repos branch policies have no built-in "require signed commits" option.
- Azure Artifacts provides feeds for packages and build dependencies.

Grant permissions through groups where possible. Protect service connections and variable groups, and separate approval for production deployments from code contribution rights.

## Common pitfalls

- Generating an Ed25519 key out of habit (because it worked on GitHub) and getting a confusing rejection from Azure Repos, which accepts only RSA keys for SSH.
- Leaving a personal access token at a long default expiration for a CI pipeline instead of rotating it — an unrotated token sitting for months is easy for an admin to spot in the audit log, but only if someone looks.
- Treating a PAT as a long-term service credential. Microsoft explicitly recommends moving automated workloads to a service principal or managed identity instead.

## Exercise

Create a personal access token scoped to **Code (Read & write)** for one project, with a 7-day expiration. Use it to authenticate one `git push` over HTTPS, then check the organization's audit log for the corresponding `PatCreated` event.

## References

- Microsoft Learn — [Use personal access tokens to authenticate](https://learn.microsoft.com/en-us/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate)
- Microsoft Learn — [Use SSH key authentication](https://learn.microsoft.com/en-us/azure/devops/repos/git/use-ssh-keys-to-authenticate)
- Microsoft Learn — [Set and manage branch policies](https://learn.microsoft.com/en-us/azure/devops/repos/git/branch-policies?view=azure-devops)
- Microsoft Learn — [About authentication, authorization, and security policies](https://learn.microsoft.com/en-us/azure/devops/organizations/security/about-security-identity)
