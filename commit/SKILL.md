---
name: commit
description: >-
  Create Git commits following project conventions for commit messages, branch naming, and commit practices.
  This skill is mandatory for every Git commit operation.
  **IMPORTANT**: You MUST consult this skill BEFORE attempting any Git commit operations.
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: git-commit
---

# Commit Skill

You MUST create Git commits in this project according to the conventions defined below.

## Requirement Keywords

The keywords "MUST", "MUST NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 ([RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119) and [RFC 8174](https://datatracker.ietf.org/doc/html/rfc8174)).
Only uppercase usage carries these special meanings.
Lowercase usage has its normal English meaning.

## Trigger

You MUST activate this skill whenever you are creating or amending Git commits, or when you need to produce a commit message or configure Git hooks.

## Commit Message Format

The commit message subject line MUST follow the [Conventional Commits](https://www.conventionalcommits.org/) format:

```plain
<type>[optional scope]: <description>
```

- Type and scope (optional) MUST be all-lowercase.
- The description MUST be in sentence case: if it starts with a letter, that letter MUST be uppercase.
- Do not end the description with a period.

### Allowed Types

The type field MUST be one of the following:

- `build`: Changes that affect the build system or external dependencies
- `ci`: Changes to CI configuration files and scripts
- `docs`: Documentation-only changes
- `feat`: A new feature
- `fix`: A bug fix
- `perf`: A code change that improves performance
- `refactor`: A code change that neither fixes a bug nor adds a feature
- `style`: Changes that do not affect the meaning of the code (white-space, formatting, missing semi-colons, etc.)
- `test`: Adding missing tests or correcting existing tests

No other type values are permitted.

## Prompt Notes

Every commit MUST contain one or more [notes](https://git-scm.com/docs/git-notes) using the `prompt` ref.
This note MUST contain the verbatim prompt that was used to generate the commit.

To add a prompt note to the most recent (`HEAD`) commit, run:

```bash
git notes --ref=prompt add -m "<prompt>"
```

To add a prompt note to a specific commit, run:

```bash
git notes --ref=prompt add -m "<prompt>" <commit-sha>
```

If multiple prompts were involved in generating a single commit, add one note for each.
When amending a commit, add a new note in the `prompt` ref.
When squashing or fixing up commits, include all prompts in the surviving commit.

## External References

If you consulted external references to create the commit, you MUST include a `References:` section in the commit message body.
List the URI of every external resource used.

## Commit Message Body

The commit message body MUST:

- Explain what and why, not how.
- Use the imperative mood ("Add X", not "Added X" or "Adding X").
- Start with a blank line after the subject.
- Include `Assisted-by: <tool>/<model>` on its own line.
- Include a `References:` section if external resources were consulted.

## Mandatory Commit Requirements

- You MUST include `Assisted-by: <tool>/<model>` in the commit message.
- You MUST NOT include emoji in commit messages.
- All commits MUST be independently testable and correct.
- Series are always unsquashed; each commit MUST be independently testable and correct.
- You MUST NOT commit to the `master` or `main` branch directly.
- All modifications require a topic branch.
- You MUST NOT amend commits you did not create.
- You MUST NOT bypass Git hooks (never use `--no-verify`).
- You MUST run `git config core.hooksPath .githooks` to enable pre-commit and pre-push hooks.

## Mandatory Commit Process

0. If you are on `main` or `master`, create a suitably named topic branch and check it out.
1. Stage your changes with `git add`.
2. Create the commit with a subject and body following the format above.
3. Add prompt notes to the `prompt` ref.
4. Verify the commit with `git log` to ensure it follows all conventions.
5. Do NOT push the commit or branch to a remote unless explicitly instructed.

## Example Commit Message

```patch
feat: Add dark mode toggle to settings page

- Implement dark mode component
- Add theme context for state management
- Update styling for dark theme

References:
https://accessibility.example.com/why-you-should-include-a-dark-mode-toggle
https://css-reference.example.com/dark-mode-toggle

Assisted-by: opencode/qwen3-coder-30b
```

## Example Commit Notes

```markdown
Add a dark mode component.
```

```markdown
Add a user-facing toggle to enable dark mode.
```

## Verification

Before completing a commit, confirm:

- The subject line matches `<type>[scope]: <description>` format exactly
- The type is one of the allowed values listed above
- The subject is all-lowercase type/scope with sentence-case description
- The body explains what and why
- `Assisted-by: <tool>/<model>` is present
- `References:` section is present if external resources were consulted
- A prompt note was added to the `prompt` ref
- The commit was not made to `master` or `main`
- The commit was not pushed to a remote
