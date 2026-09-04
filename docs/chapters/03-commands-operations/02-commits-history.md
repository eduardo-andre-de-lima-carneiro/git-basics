# 3.2 Commits and History

Useful inspection commands include:

```bash
git log --oneline --decorate --graph
git show <commit>
git diff <commit-a> <commit-b>
```

## Reading the output

- [`git log --oneline`](https://git-scm.com/docs/git-log) is shorthand for `--pretty=oneline --abbrev-commit`: one line per commit, with a short hash instead of the full 40-character one.
- `--decorate` prints the ref names — branch tips and tags — pointing at each commit shown, so you can see where `main`, `HEAD`, or a tag currently sits in the graph.
- `--graph` draws a text-based graph on the left of the output, showing how branches diverged and merged; it is most useful combined with `--oneline --decorate`.
- [`git show <commit>`](https://git-scm.com/docs/git-show) displays a single commit's log message together with its full diff — the fastest way to inspect one change without listing history around it.
- `git diff <commit-a> <commit-b>` compares two arbitrary commits directly, independent of the branch structure between them.

## Focused commits and messages

Prefer focused commits that represent one logical change — a commit that mixes a bug fix with a formatting pass is harder to review, revert, or `git log --follow` later. History is easier to navigate when commit messages use an imperative, specific description ("Fix null check in parser", not "fixes").

A widely used convention for structuring that message is [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/): a `type(scope): description` prefix (`fix:`, `feat:`, `docs:`, …) that makes history skimmable with `git log --oneline` and lets tooling generate changelogs automatically. It is optional here, but worth adopting if your project doesn't already have a message convention.

## Common pitfalls

- An abbreviated hash from `--oneline` is unambiguous only relative to the objects that currently exist in your repository; don't hardcode it in documentation meant to outlive the branch.
- Rewriting the message or content of a commit already pushed to a shared branch requires a force-push and coordination with anyone who fetched it — see [3.5 Undoing changes safely](05-undo.md) before doing this.

## Exercise

In a practice repository, make three small commits. Run `git log --oneline --decorate --graph --all` and identify the ref names shown. Use `git show` on the middle commit to see just its diff, then `git diff` between the first and last commit to see the cumulative change.

## References

- Git reference — [git-log](https://git-scm.com/docs/git-log)
- Git reference — [git-show](https://git-scm.com/docs/git-show)
- Git reference — [git-diff](https://git-scm.com/docs/git-diff)
- Pro Git (2nd ed.) — [Viewing the Commit History](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History)
- [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)
