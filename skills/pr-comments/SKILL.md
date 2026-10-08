---
name: pr-comments
description: "Fetch GitHub pull request reviews and comments, and summarize which review threads are resolved or open. Use when the user asks for PR comments, review comments, requested changes, unresolved reviews, or which review threads are still open. Accepts a PR URL, owner/repo#number, or a PR number in the current repo."
argument-hint: "PR URL, owner/repo#number, or number"
---

# Pull request comments

Fetch every comment on a pull request and show which review threads are still open.

## When to use

- The user pastes a pull request URL and wants the comments.
- The user asks which review comments are resolved or still open.
- The user types `/pr-comments`.

## Steps

1. Run [scripts/pr-comments](scripts/pr-comments) with the pull request URL, `owner/repo#number`, or a PR number.
2. If the user gives only a number, run the script from that git repo, not from a parent folder.
3. Do not use MCP or other GitHub tools for this. The script uses the local `gh` CLI.
4. Show the script output to the user. Keep author, time, file, line, resolved or open, and the comment body.
5. Do not edit code unless the user asks for an action plan or a fix.
6. If a section is empty, say so. Do not invent comments.

## Example

```bash
./scripts/pr-comments https://github.com/owner/repo/pull/123
```
