---
name: commit
description: >-
  Create Git commits following project conventions for commit messages, branch naming, and commit practices.
  Use this skill when the user wants to create a commit or needs guidance on proper Git commit formatting, including conventional commit types, required metadata like Assisted-by, and project-specific requirements like topic branches and pre-commit hooks.
  **IMPORTANT**: This skill MUST be consulted BEFORE attempting any Git commit operations.
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: git-commit
---

# Commit Skill

This skill provides instructions for creating Git commits in this project according to the project's conventions.

## When to use this skill

Use this skill when:

- Creating or amending Git commits
- Needing guidance on proper commit message structure with type prefixes
- Needing to understand Git hook requirements and commit validation practices

## Commit Message Format

Commit message subjects must follow the [Conventional Commits](https://www.conventionalcommits.org/) format:

```plain
<type>[optional scope]: <description>
```

The allowed types are:

- build: Changes that affect the build system or external dependencies
- ci: Changes to our CI configuration files and scripts
- docs: Documentation only changes
- feat: A new feature
- fix: A bug fix
- perf: A code change that improves performance
- refactor: A code change that neither fixes a bug nor adds a feature
- style: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc.)
- test: Adding missing tests or correcting existing tests

## Notes

Every commit must contain one or more [notes](https://git-scm.com/docs/git-notes), using the `prompt` ref.
This note must contain the verbatim prompt that was used to generate the commit.

If multiple prompts were involved in generating a single commit, include them all.
When amending a commit, add a new note in the `prompt` ref.
When squashing or fixing up commits, add notes containing all prompts to the surviving commit.

## Commit Requirements

- Always include `Assisted-by: <tool>/<model>` in the commit message
- Never include emoji in commit messages
- All commits must be independently testable and correct
- Series are always unsquashed; each commit must be independently testable and correct
- Do not commit to the `master` or `main` branch directly
- All modifications require a topic branch
- Never amend commits you did not create
- Never bypass Git hooks (in other words: never use the `--no-verify` option)
- Use the `git config core.hooksPath .githooks` configuration to enable pre-commit and pre-push hooks

## Commit Process

0. If you're currently on `main` or `master`, create a suitably named topic branch and check it out
1. Ensure your changes are staged with `git add`
2. Create the commit with a descriptive message following the format above
3. Verify your commit with `git log` to ensure it follows the conventions
4. Never push any commit or a branch to a remote unless explicitly instructed to

## Example Commit Message

```patch
feat: Add dark mode toggle to settings page

- Implement dark mode component
- Add theme context for state management
- Update styling for dark theme

Assisted-by: opencode/qwen3-coder-30b
```

## Example Commit Notes

```markdown
Add a dark mode component.
```

```markdown
Add a user-facing toggle to enable dark mode.
```
