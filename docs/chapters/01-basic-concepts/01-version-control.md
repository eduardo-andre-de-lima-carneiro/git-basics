# 1.1 Version Control Systems

Version control records changes to files over time. It lets a team compare revisions, identify authors, restore earlier states, and work on separate changes without overwriting one another.

## The problem it solves

Without version control, filenames such as `project-final-final-2` become the history. Git keeps the history in a structured repository instead.

## Three generations of version control

Version control systems fall into three broad categories, described in the Pro Git book's [overview of version control](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control):

- **Local VCS** (e.g. RCS) keep a patch database on a single machine. There is no collaboration, and no protection if that machine is lost.
- **Centralized VCS** (e.g. CVS, Subversion) store the full history on one server; clients check out working copies. Collaboration works, but the server is a single point of failure — if it goes down, or its database is corrupted without a backup, the project's history can be lost.
- **Distributed VCS** (e.g. Git, Mercurial) give every clone the complete history. Any clone can restore the project if a server is lost, and most day-to-day operations do not need the network.

## Common pitfalls

- **Version control is not a backup service.** A backup copies files; version control also records *why* something changed and lets you compare, blame, and revert individual changes.
- **A repository is not the same as a single checked-out copy.** Deleting your working copy does not delete history that is already committed and safely stored elsewhere (locally or on a remote).

## Practice

Create a small text file, change it twice, and write down what you would need to know to recover the first version. That list is the value version control provides.

## References

- Pro Git (2nd ed.) — [About Version Control](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)
- Git reference manual — [git-scm.com/docs](https://git-scm.com/docs)
