# 4.1 Integration Fundamentals

Hosted platforms add collaboration and delivery services around a Git repository. The local commands remain familiar; the platform supplies identity, permissions, review, automation, and project visibility.

## The common flow

1. Create or select a remote repository.
2. Connect the local repository with `git remote add origin <repository-url>`.
3. Push a branch with `git push -u origin <branch-name>`.
4. Open a pull request or merge request for review.
5. Let required checks run before merging.
6. Delete the short-lived branch after the change is integrated.

## Choose HTTPS or SSH

HTTPS is simple to start with and normally uses a personal access token instead of an account password. SSH uses a key pair and is convenient for frequent command-line work. Never put tokens, private keys, or credentials in a repository.

## What to configure

At minimum, agree on the default branch, branch protection rules, review requirements, status checks, issue linking, and who can push or merge. These policies are part of the team's delivery process, not merely platform decoration.
