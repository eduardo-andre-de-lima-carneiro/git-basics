# 4.3 GitLab

GitLab provides Git repositories with merge requests, Issues, CI/CD pipelines, Package Registry, and security dashboards in one platform.

## Connect and publish

Create a project on GitLab, then run locally:

```bash
git remote add origin https://gitlab.com/GROUP/PROJECT.git
git push -u origin main
```

Use your actual group, project, and default branch names. Review the remote with `git remote -v` before pushing.

## Authentication

For HTTPS, GitLab accepts [any non-empty string as the username and a personal access token as the password](https://docs.gitlab.com/user/profile/personal_access_tokens/). A token is *required*, not optional, once two-factor authentication or SSO is enabled on the account. New tokens must carry an expiration date; GitLab applies a 365-day default if you don't set one, and administrators on the Ultimate tier can enforce a shorter maximum.

For frequent command-line work, an [SSH key](https://docs.gitlab.com/user/ssh/) avoids re-entering a token on every push. GitLab recommends the Ed25519 key type over RSA: `ssh-keygen -t ed25519 -C "<comment>"`. Newly added keys are screened against a list of known-compromised keys before GitLab accepts them.

GitLab also supports [two-factor authentication](https://docs.gitlab.com/user/profile/account/two_factor_authentication/) — passkeys, OTP apps, WebAuthn security keys, or email codes — which a group or a self-managed instance can require for every member.

## Useful integrations

- Merge requests combine review, approvals, discussions, and pipeline results.
- `.gitlab-ci.yml` defines CI/CD jobs, stages, artifacts, and deployment rules.
- [Protected branches](https://docs.gitlab.com/user/project/repository/branches/protected/) and environments control who can merge or deploy.
- Deploy tokens, project access tokens, and runners support automation.
- Webhooks and integrations notify issue trackers, chat tools, and security systems.

Use masked and protected CI/CD variables for credentials. Keep runners patched, restrict privileged runners, and give tokens only the scopes required by their job.

## Common pitfalls

- Forgetting that GitLab silently applies a 365-day expiration to a personal access token created without one — a token that looks like it has "no expiration" will still stop working a year later.
- Registering a WebAuthn security key against one GitLab hostname (say, a self-managed instance) and expecting it to also work on `gitlab.com` — WebAuthn registrations are tied to the hostname, so each one needs its own registration.
- Committing without ever configuring commit signing, then being surprised a protected branch's "verified" badge never appears; GitLab checks the signature against a key already added to the account.

## Exercise

Generate an Ed25519 SSH key, add the public key to your GitLab account, then clone a project over SSH and confirm `git push` no longer prompts for a token.

## References

- GitLab Docs — [Personal access tokens](https://docs.gitlab.com/user/profile/personal_access_tokens/)
- GitLab Docs — [SSH keys](https://docs.gitlab.com/user/ssh/)
- GitLab Docs — [Two-factor authentication](https://docs.gitlab.com/user/profile/account/two_factor_authentication/)
- GitLab Docs — [Protected branches](https://docs.gitlab.com/user/project/repository/branches/protected/)
- GitLab Docs — [Signed commits](https://docs.gitlab.com/user/project/repository/signed_commits/)
