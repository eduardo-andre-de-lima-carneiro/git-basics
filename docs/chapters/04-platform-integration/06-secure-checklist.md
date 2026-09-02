# 4.6 Secure Integration Checklist

Before calling an integration ready, check the following:

- The remote URL is correct and does not contain a secret.
- Authentication uses SSH keys, tokens, or an application identity with limited scope.
- The default branch is protected against accidental direct pushes.
- Pull or merge requests require appropriate review and passing automated checks.
- CI/CD secrets are stored in the platform's secret manager.
- Dependency, secret, and vulnerability scanning are enabled where appropriate.
- Production deployment requires a separate approval or protected environment.
- Webhooks validate their signatures and send only the data they need.
- Access is reviewed when a person, token, runner, or service changes role.

Integration is successful when it makes delivery more traceable and repeatable without making credentials or production changes easier to misuse.
