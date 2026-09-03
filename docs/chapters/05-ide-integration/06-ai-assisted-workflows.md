# 5.6 AI-Assisted Workflows

This section is optional. Many editors now offer AI assistants that can draft commit messages, summarize a diff, explain a conflict, or suggest a pull request description.

## Where it shows up

- **Visual Studio Code** and **Visual Studio**: GitHub Copilot can generate a commit message from staged changes and draft pull request text.
- **JetBrains IDEs**: the AI Assistant offers "Generate Commit Message" in the Commit tool window.
- Standalone clients such as GitKraken expose similar commit-message helpers.

## How to use it safely

- Treat generated text as a first draft. Read the diff yourself and edit the message so it says *why*, not just *what*.
- Never let an assistant stage or commit changes you have not reviewed.
- Assume the diff and file contents may be sent to an external service. Do not use these features on repositories with secrets or restricted code unless your organization approves it.
- Keep the message conventions your team already agreed on; an assistant does not know them unless told.

## Exercise

Stage a small change in a practice repository and ask your editor's assistant for a commit message. Rewrite it in your own words to explain the reason for the change, then commit.
