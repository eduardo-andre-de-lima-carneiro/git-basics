# 4.2 GitHub

GitHub combines hosted Git repositories with pull requests, Issues, Actions, Projects, Packages, and security features.

## Connect and publish

Create an empty repository on GitHub, then run locally:

```bash
git remote add origin https://github.com/OWNER/REPOSITORY.git
git push -u origin main
```

Replace `OWNER`, `REPOSITORY`, and `main` with your values. Do not initialize the GitHub repository with a second README when your local repository already has one, unless you plan to reconcile the histories.

## Authentication

GitHub [removed password authentication for Git operations in August 2021](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/about-authentication-to-github); the HTTPS prompt now expects a token, not your account password. Choose one of:

- **A [personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)** used in place of the password. GitHub recommends the newer *fine-grained* tokens — scoped to specific repositories and specific permissions — over *classic* tokens, which grant broad, account-wide scopes like `repo`. A classic token left unused is auto-revoked after a year; a fine-grained token must be given an expiration when you create it.
- **An [SSH key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)** — GitHub recommends generating an Ed25519 key — added to your account once, after which `git push`/`git pull` need no further credential prompt.
- **GitHub CLI (`gh auth login`) or Git Credential Manager**, which GitHub's own docs suggest ahead of minting a token by hand, since they manage the token's storage and refresh for you.

GitHub also [requires two-factor authentication (2FA)](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication) for accounts that contribute code, using a TOTP app, a hardware security key, or GitHub Mobile.

## Useful integrations

- Pull requests provide review, discussion, required approvals, and status checks.
- GitHub Actions can test, scan, package, and deploy on pushes or pull requests.
- [Branch protection rules](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches) can require reviews, passing checks, and signed commits.
- Environments can restrict deployments and protect production secrets.
- Webhooks and the API connect repository events to external systems.

Use least-privilege fine-grained personal access tokens or GitHub Apps. Store automation secrets in repository or environment secrets, never in workflow files or source code.

## Common pitfalls

- A classic PAT copy-pasted into a script with the full `repo` scope, when the script only ever pushes to one repository — a leak of that token compromises every repository the account can reach. Use a fine-grained token scoped to the one repository instead.
- Setting a PAT's expiration and forgetting about it: the day it lapses, `git push` fails with an authentication error that looks like a broken remote rather than an expired credential.
- Generating an SSH key without a passphrase on a shared machine. GitHub can verify the key came from you, but it cannot protect a private key file that anyone with disk access can read.

## Exercise

Create a fine-grained personal access token scoped to one practice repository, with **Contents: Read and write** permission and a short expiration (7 days). Use it once to `git push` over HTTPS, then revoke it early and confirm the next push fails with an authentication error.

## References

- GitHub Docs — [About authentication to GitHub](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/about-authentication-to-github)
- GitHub Docs — [Managing your personal access tokens](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)
- GitHub Docs — [Connecting to GitHub with SSH](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
- GitHub Docs — [About two-factor authentication](https://docs.github.com/en/authentication/securing-your-account-with-two-factor-authentication-2fa/about-two-factor-authentication)
- GitHub Docs — [About protected branches](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-protected-branches/about-protected-branches)
