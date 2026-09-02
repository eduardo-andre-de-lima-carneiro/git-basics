# 2.2 Configure Identity and Defaults

Set the name and email that Git records on new commits:

```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
```

Review the effective configuration with `git config --list --show-origin`.
