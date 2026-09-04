# 2.1 Install Git

Git 2.23 or newer is recommended for the `git switch` and `git restore` examples used later. Older versions may require equivalent commands such as `git checkout`. Install Git using the package manager or installer recommended for your operating system, listed below, or browse every option on the [official downloads page](https://git-scm.com/downloads).

## Windows

Install with [winget](https://learn.microsoft.com/en-us/windows/package-manager/winget/install), which ships with modern Windows 10/11:

```bash
winget install --id Git.Git -e --source winget
```

Alternatively, download the installer from [git-scm.com/downloads/win](https://git-scm.com/downloads/win). During setup, keep the default "Git from the command line and also from 3rd-party software" option so `git` is added to your `PATH`; otherwise later commands in this course will fail with "command not found" in a fresh terminal.

## macOS

If you use [Homebrew](https://docs.brew.sh/Installation), install with:

```bash
brew install git
```

macOS also offers Git through the Xcode Command Line Tools:

```bash
xcode-select --install
```

The command line tools install a functional but often older Git than Homebrew's. If you need a specific recent version, prefer Homebrew and run `brew upgrade git` periodically.

## Linux

Use your distribution's package manager. On Debian and Ubuntu:

```bash
sudo apt install git
```

On Fedora and other `dnf`-based distributions:

```bash
sudo dnf install git
```

Distribution repositories can lag behind the latest Git release by months. If you need a newer version on Ubuntu, add the [git-core PPA](https://git-scm.com/downloads/linux) before installing; on Fedora, `dnf` generally tracks upstream closely enough that this is rarely necessary.

## Verify the installation

```bash
git --version
```

The exact version may vary. The command should print a version instead of an error. If it prints "command not found" right after a Windows install, re-open the terminal (or reboot) so the updated `PATH` takes effect.

## After installing

A freshly installed Git has no identity and no default branch name configured. Before making your first commit, set them up as described in [Configure identity and defaults](02-configure.md) — an unconfigured `user.email` produces commits attributed to a placeholder address instead of you.

## Common pitfalls

- **Installing from an unofficial source.** Only use the package managers and installer above, or the [official downloads page](https://git-scm.com/downloads); unofficial "Git installer" bundles from search results can be outdated or unsafe.
- **Multiple Git installations.** Installing Git through more than one method (e.g., Xcode tools and Homebrew) can leave an older `git` earlier on `PATH`. Run `which git` (macOS/Linux) or `where git` (Windows) to confirm which binary actually runs.
- **Skipping the version check.** Always run `git --version` right after installing — it is the cheapest way to confirm the install succeeded before troubleshooting anything else.

## Exercise

Install Git for your operating system using the method above, then run `git --version` and confirm it reports 2.23 or newer. If it reports an older version, upgrade using the same package manager (`brew upgrade git`, `sudo apt update && sudo apt upgrade git`, or `winget upgrade --id Git.Git`).

## References

- Git — [Downloads](https://git-scm.com/downloads)
- Pro Git (2nd edition) — [Installing Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
- Homebrew — [Installation](https://docs.brew.sh/Installation)
- Microsoft Learn — [Install winget](https://learn.microsoft.com/en-us/windows/package-manager/winget/install)
