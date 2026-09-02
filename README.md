# Git Basics

> Learn Git by understanding what it is, practicing what it does, and building confidence one small step at a time.

Git Basics is a practical, guided course for people who are new to Git, moving from Subversion, or looking for a clearer mental model of everyday version control.

[Start the course](menu.md) | [Choose your language](#languages) | [Contribute](CONTRIBUTING.md)

## Why this course exists

Git documentation can be technically accurate and still feel difficult to enter. This project turns the essential ideas into a guided path: short explanations, real commands, visible results, and exercises that can be practiced in a temporary repository.

The goal is not to memorize a list of commands. The goal is to understand the state of your project, make intentional changes, and recover calmly when something goes wrong.

## What you will learn

- How version control protects and explains the history of a project.
- How Git's working tree, staging area, commits, branches, and remotes fit together.
- How to install and configure Git for personal or team projects.
- How to inspect changes before committing them.
- How to create branches, synchronize with remotes, and collaborate safely.
- How to choose the right recovery command for an unwanted change.

## Course map

| Chapter                                                                                    | Focus                                            | You will practice                                                           |
| ------------------------------------------------------------------------------------------ | ------------------------------------------------ | --------------------------------------------------------------------------- |
| [1. Basic concepts](docs/chapters/01-basic-concepts/README.md)                             | The ideas behind version control and Git         | Thinking in snapshots, history, and project states                          |
| [2. Installation and configuration](docs/chapters/02-installation-configuration/README.md) | Getting Git ready to use                         | Checking the installation, identity, defaults, and repositories             |
| [3. Commands and operations](docs/chapters/03-commands-operations/README.md)               | Building a dependable daily workflow             | Commits, branches, remotes, merges, exercises, and recovery                 |
| [4. Platform integration](docs/chapters/04-platform-integration/README.md)                 | Connecting Git to hosted collaboration platforms | Pull requests, merge requests, permissions, automation, and secure delivery |

## A quick first practice

Once Git is installed, create a disposable practice repository:

```bash
mkdir git-practice
cd git-practice
git init
printf "My first Git file\n" > notes.txt
git add notes.txt
git commit -m "Add first practice file"
git log --oneline
```

You have just created a repository, prepared a change, recorded a commit, and inspected its history. Chapter 1 explains what happened at each stage.

## How to use the documentation

1. Begin with the [documentation menu](menu.md).
2. Read Chapter 1 before diving into command memorization.
3. Complete the setup steps in Chapter 2.
4. Work through Chapter 3 in a disposable repository.
5. Explore Chapter 4 for the platform used by your team.
6. Use the [glossary](docs/glossary.md) whenever a term is unfamiliar.

Every lesson is a standalone Markdown file, linked with relative paths so it can be read directly on GitHub.

## Languages

The course is available in four languages:

- [English](menu.md)
- [Français](docs/i18n/fr/README.md)
- [Português (Brasil)](docs/i18n/pt-br/README.md)
- [Español](docs/i18n/es/README.md)

## Project values

- **Practical:** examples should lead to something the learner can observe.
- **Approachable:** explain the idea before introducing the command.
- **Safe:** use disposable repositories and make destructive operations explicit.
- **Open:** keep the documentation free, reusable, and easy to improve.

## Contributing

Found a confusing explanation, a missing exercise, or a broken link? Read the [contribution guide](CONTRIBUTING.md) and help make the next learner's first Git experience better.

## Origin

This course grew out of a DevSecOps experience supporting teams that were migrating from Subversion to Git. Official documentation and reference sites were useful, but some learners needed a more guided and practical route into the subject. Git Basics was created to provide that route and to make the learning process easier to share.

The project is intentionally collaborative. Feedback, corrections, examples, and translations are welcome.
