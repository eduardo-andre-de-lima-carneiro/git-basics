# 1.2 Why Git

Git is distributed: each clone contains the project history needed for most local operations. This makes commits, comparisons, and branch creation fast and available offline.

Git also provides explicit checkpoints called commits. A good commit answers: what changed, and why?

## Where Git came from

Git was created in 2005 by Linus Torvalds and the Linux kernel community, after the proprietary tool the kernel project had been using, BitKeeper, stopped being available for free. The design goals were speed, a simple design, strong support for non-linear (branching) development, being fully distributed, and being able to handle large projects such as the Linux kernel efficiently. See the Pro Git book's [short history of Git](https://git-scm.com/book/en/v2/Getting-Started-A-Short-History-of-Git) for the full story.

## Snapshots, not diffs

Unlike systems that store a list of file-based changes, Git stores a snapshot of the entire project at every commit; a file that has not changed is simply linked to the previous identical version instead of being duplicated. Every object is checksummed before it is stored — historically with SHA-1, with SHA-256 available as a newer option through Git's [hash-function transition](https://git-scm.com/docs/hash-function-transition) — so silent corruption or tampering is detectable. See [What is Git?](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F) in the Pro Git book.

## Git vs. Subversion vs. Mercurial

| | Git | Subversion (SVN) | Mercurial |
|---|---|---|---|
| Model | [Distributed](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control) | [Centralized](https://subversion.apache.org/) | [Distributed](https://www.mercurial-scm.org/) |
| Branching cost | A branch is a movable pointer to a commit — [near-instant to create](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell) | A [cheap server-side copy](https://svnbook.red-bean.com/en/1.7/svn.branchmerge.using.html), but creating and using it still requires the central server | Cheap; branches and bookmarks live in the local clone |
| Offline capability | Full — commit, diff, log, and branch all work without a network | Limited — most operations need to contact the server | Full — "every clone contains the whole project history" |
| Typical use today | Default choice for most new projects; used by [96% of professional developers](https://git-scm.com/about) (2022 Stack Overflow survey) | Still found in some enterprises wanting centralized access control over history | Niche; mostly legacy deployments, largely superseded by Git |

## Common pitfalls

- **A commit is not a diff.** Git records the full staged snapshot at commit time, not just what changed — that is what makes checking out an old commit a direct file-tree operation instead of replaying a chain of patches. See [Recording Changes to the Repository](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository).

## Key idea

Git is not only a file backup system. It is a tool for building, inspecting, and sharing a timeline of intentional changes.

## References

- Pro Git (2nd ed.) — [A Short History of Git](https://git-scm.com/book/en/v2/Getting-Started-A-Short-History-of-Git)
- Pro Git (2nd ed.) — [What is Git?](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F)
- Git reference — [Git hash-function transition](https://git-scm.com/docs/hash-function-transition)
- git-scm.com — [About Git](https://git-scm.com/about)
- Apache Subversion — [subversion.apache.org](https://subversion.apache.org/)
- Mercurial — [mercurial-scm.org](https://www.mercurial-scm.org/)
