# 4.6 Secure Integration Checklist

Before calling an integration ready, check the following:

- The remote URL is correct and does not contain a secret.
- Authentication uses SSH keys, tokens, or an application identity with limited scope — never an account password; every platform in this chapter has removed or is removing password authentication for Git over HTTPS.
- Two-factor or multi-factor authentication is enabled on every human account with push or merge access, not just admin accounts.
- Personal access tokens carry the narrowest scope the task needs, a short expiration, and a rotation plan — a token that "just works forever" is a token nobody is watching.
- SSH keys use a modern algorithm (Ed25519 where the platform accepts it; Azure Repos is the exception and requires RSA) and are rotated or removed when a person changes role or leaves the team.
- The default branch is protected against accidental direct pushes.
- Pull or merge requests require appropriate review and passing automated checks.
- Commit signing (GPG, SSH, or the platform's supported method) is enabled where the team wants a verified badge as proof of authorship, understanding that not every platform enforces it the same way — GitHub and GitLab can require signed commits as a branch policy, while Azure Repos currently has no equivalent branch-policy toggle.
- CI/CD secrets are stored in the platform's secret manager, never in a workflow file or a script.
- Dependency, secret, and vulnerability scanning are enabled where appropriate.
- Production deployment requires a separate approval or protected environment.
- Webhooks validate their signatures and send only the data they need.
- Access is reviewed when a person, token, runner, or service changes role — and immediately when one leaves.

## Account-level protections

Each platform documents its own current requirement and setup:

- GitHub [requires 2FA](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication) for accounts that contribute code, and supports [signing commits with GPG, SSH, or S/MIME](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification).
- GitLab supports [group- or instance-enforced 2FA](https://docs.gitlab.com/user/profile/account/two_factor_authentication/) and [signed commits via SSH, GPG, or X.509](https://docs.gitlab.com/user/project/repository/signed_commits/).
- Azure DevOps ties multi-factor authentication to how the organization is backed: [Microsoft Entra ID sign-in inherits Entra's MFA and Conditional Access policies](https://learn.microsoft.com/en-us/azure/devops/organizations/security/about-security-identity), and accounts on a Microsoft account can enable 2FA directly.
- Bitbucket Cloud supports [two-step verification](https://support.atlassian.com/bitbucket-cloud/docs/enable-two-step-verification/) via an authenticator app or a security key, independent of which Git credential (API token or SSH key) the account uses.

## Common pitfalls

- Treating "2FA is required for the organization" as equivalent to "2FA is enabled for every member" — an enforcement setting and individual enrollment are two different checks, and one can lag the other.
- Requiring signed commits on GitHub or GitLab but never showing contributors how to set up SSH or GPG signing locally, so the requirement blocks legitimate pushes instead of catching a real problem.
- Auditing tokens and keys once at project setup and never again. Rotation is a recurring task, not a one-time checklist item.

Integration is successful when it makes delivery more traceable and repeatable without making credentials or production changes easier to misuse.

## References

- GitHub Docs — [About two-factor authentication](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication)
- GitHub Docs — [About commit signature verification](https://docs.github.com/en/authentication/managing-commit-signature-verification/about-commit-signature-verification)
- GitLab Docs — [Two-factor authentication](https://docs.gitlab.com/user/profile/account/two_factor_authentication/)
- GitLab Docs — [Signed commits](https://docs.gitlab.com/user/project/repository/signed_commits/)
- Microsoft Learn — [About authentication, authorization, and security policies](https://learn.microsoft.com/en-us/azure/devops/organizations/security/about-security-identity)
- Atlassian Support — [Enable two-step verification](https://support.atlassian.com/bitbucket-cloud/docs/enable-two-step-verification/)
