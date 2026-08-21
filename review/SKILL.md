---
name: review
description: >-
  Review a pull request by examining each commit for accuracy: verify that commit
  messages accurately describe their changes, assess whether messages include a
  rationale for the change, and check that the commit body is consistent with
  the diff. IMPORTANT: This skill MUST be consulted BEFORE performing any PR
  commit review.
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: code-review
---

# Commit Review Skill

This skill provides instructions for reviewing pull request commits to assess the quality and accuracy of commit messages and their alignment with the actual changes.

## When to use this skill

Use this skill when:

- Reviewing a pull request and the PR contains multiple commits
- Needing to assess whether commit messages accurately describe their changes
- Checking whether commits include sufficient rationale for the changes made
- Verifying that commit messages are consistent with the actual diff

## Pre-review steps

1. Fetch the PR's commit list with `git log` or the GitHub API
2. For each commit, retrieve the diff using `git show <commit>` or `git diff <parent> <commit>`
3. Evaluate each commit independently using the criteria below

## Evaluation criteria

### 1. Message accuracy

The commit subject line must accurately summarize the change. Check for:

- Does the subject describe what changed, not just that something changed?
- Are file paths, function names, or component names in the subject correct?
- Does the subject avoid vague language like "fix things", "updates", or "misc"?
- Does the subject follow Conventional Commits format (`type: description`)?

### 2. Rationale assessment

The commit message (subject body) should explain *why* the change was made. Look for:

- A description of the problem or motivation that prompted the change
- Context about the decision, especially for non-obvious refactorings
- References to issues, bugs, or requirements when applicable
- An explanation of *what* was changed and *why*, not just *what* was changed

A commit message that only states "what" without "why" is incomplete unless the change
is so self-evident that no rationale is needed (e.g., a typo fix).

### 3. Diff consistency

The commit message must match the actual code changes:

- Does the message claim to change something that isn't in the diff?
- Does the diff change something the message doesn't mention?
- Are the listed affected files actually in the diff?
- Is the scope of the change in the message proportional to the diff?

### 4. Conventional Commits compliance

Subjects must use the standard type prefixes:

| Type       | Meaning                                              |
|------------|-------------------------------------------------------|
| `feat`     | A new feature                                         |
| `fix`      | A bug fix                                             |
| `perf`     | A performance improvement                               |
| `refactor` | A code change with no bug fix or feature                |
| `style`    | Formatting, whitespace, semicolons — no code meaning    |
| `test`     | Adding or correcting tests                              |
| `docs`     | Documentation only                                     |
| `ci`       | CI configuration changes                                |
| `build`    | Build system or dependency changes                      |

## Posting the review

After evaluating all commits, post a single PR comment using Markdown with the following
structure:

### Header

Start with a summary verdict:

```markdown
## Commit Review

| # | Subject | Accurate? | Rationale? | Verdict |
|---|---------|-----------|------------|---------|
| 1 | feat: ... | Yes / Partial / No | Yes / No | Pass / Warning / Fail |
| 2 | fix: ... | Yes / Partial / No | Yes / No | Pass / Warning / Fail |
```

### Criteria definitions

- **Pass** — Message is accurate, includes rationale, and matches the diff.
- **Warning** — Message is mostly accurate but missing rationale or has minor
  inconsistencies with the diff.
- **Fail** — Message misrepresents the change, has no rationale for a non-trivial
  change, or has major inconsistencies with the diff.

### Detail section

For each commit that received a "Warning" or "Fail", provide a short explanation:

```markdown
### Details

#### Commit 2 — `fix: update auth handling`

**Verdict: Warning** — Rationale missing.

The message correctly describes the change (updating authentication), but the body
does not explain why the change was needed. Consider adding context about the
security issue or user-reported bug that motivated this fix.

#### Commit 4 — `refactor: clean up utils`

**Verdict: Fail** — Message does not match diff.

The subject claims a general cleanup of utils, but the diff introduces a new
`parseCurrency()` function and removes only one dead import. The scope of the
change is broader than "cleanup" suggests and would be better described as
`feat: add parseCurrency utility`.
```

### Summary

End with an overall assessment:

```markdown
### Overall

X of Y commits pass the review. Z commit(s) need attention.
```

## Writing rules

- Use one sentence per line outside of code blocks.
- Do not end lines in trailing whitespace.
- End the file with a newline character.
- No emojis in the output.
- Be concise; avoid repeating what is obvious from the diff.
