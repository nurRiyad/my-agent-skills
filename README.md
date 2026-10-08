# My Agent Skills

A personal collection of reusable skills for AI coding agents. Each skill lives
in its own folder under `skills/` and can include a `SKILL.md` plus any
supporting scripts, references, or assets.

## Create a skill

Create a folder such as `skills/my-skill/` and add a `SKILL.md` file:

```markdown
---
name: my-skill
description: Use when you need help with this task.
---

# My Skill

Explain when to use the skill and the steps the agent should follow.
```

The `name` must be lowercase kebab-case and match the skill folder name. Make
the description specific so agents can tell when the skill applies. Keep
machine-specific paths, credentials, and other secrets out of skills.

## Skills in this repository

- [`pr-body`](./skills/pr-body/SKILL.md): draft a pull request body from a branch
  diff and the repository's PR template.
- [`pr-comments`](./skills/pr-comments/SKILL.md): fetch and summarize pull
  request comments, reviews, and open or resolved review threads.

## Use this repository

This repository uses Node.js for the skills CLI. The required version is pinned
in `.nvmrc`. With NVM installed, select it before using the CLI:

```sh
nvm use
npx skills add YOUR_GITHUB_USERNAME/my-agent-skills
```

The CLI can install skills for supported agents. Review its prompts and options
to choose which agents and installation scope to use. For private repositories,
authenticate with GitHub first.

After pushing skill changes to GitHub, use the skills CLI to refresh the
installed skills on each machine. Run `npx skills --help` for the current update
options.

## Publish to GitHub

Create an empty GitHub repository, then connect and push this local repository:

```sh
git remote add origin git@github.com:YOUR_GITHUB_USERNAME/my-agent-skills.git
git push -u origin main
```
