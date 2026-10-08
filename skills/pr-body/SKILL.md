---
name: pr-body
description: "Fill a GitHub pull request body from the branch diff and the repo PR template. Use when the user asks for a PR description, PR body, PR template, or to update the pull request text from the current changes. Writes changes.diff against origin/main or origin/master, then returns markdown to paste into GitHub."
argument-hint: "Optional path to the git repo"
---

# Pull request body

Build a pull request body from the branch diff and that repo's pull request template.

## When to use

- The user wants PR text they can copy into GitHub.
- The user types `/pr-body`.
- The user asks to fill `.github/pull_request_template.md` from the current changes.

## Steps

1. Find the git repo. If the user gives a path, use it. Otherwise use the repo for the files they are working on. Do not run this in a parent folder that is not the service repo.
2. Run [scripts/commitdiff](scripts/commitdiff) with the repo path. It writes `changes.diff` at the repo root, using `origin/main` or `origin/master`, same as the user's `commitdiff` shell function.
3. Read `changes.diff`. If it is empty, stop and say there is no diff against the default branch.
4. Read the template path printed by the script. If it says none, use a short body with Summary, Why, Changes, and How to test.
5. Fill the template from the diff only. Keep the repo's headings and checklist.
6. Return one markdown block the user can paste into the GitHub pull request body.

## Rules

- Do not invent ticket numbers, test runs, reviewers, or environments.
- Leave a checklist box unchecked unless the diff shows that item is done.
- Replace the template's HTML comments with the filled text. Do not leave `<!---` comments in the output.
- Do not commit `changes.diff`.
- Do not push, and do not edit the GitHub pull request, unless the user asks.

## Example

```bash
./scripts/commitdiff /path/to/repo
```
