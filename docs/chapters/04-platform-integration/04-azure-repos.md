# 4.4 Azure Repos

Azure Repos hosts Git repositories inside Azure DevOps projects and connects naturally to Azure Boards, Pipelines, Test Plans, and Artifacts.

## Connect and publish

Create or select a repository in an Azure DevOps project, then run locally:

```bash
git remote add origin https://dev.azure.com/ORGANIZATION/PROJECT/_git/REPOSITORY
git push -u origin main
```

The exact URL can be copied from the repository's Clone action. Use Microsoft Entra authentication, SSH, or a properly scoped personal access token according to your organization's policy.

## Useful integrations

- Pull requests support reviewers, branch policies, linked work items, and build validation.
- Azure Pipelines can build, test, scan, and deploy from repository events.
- Azure Boards links commits and pull requests to work items for traceability.
- Branch policies can require reviewers, successful builds, and comment resolution.
- Azure Artifacts provides feeds for packages and build dependencies.

Grant permissions through groups where possible. Protect service connections and variable groups, and separate approval for production deployments from code contribution rights.
