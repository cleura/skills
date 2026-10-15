---
name: write-markdown
description: >-
  Create or modify Markdown documentation in this project following the project's style guide and conventions.
  This skill is mandatory for all Markdown file operations.
  **IMPORTANT**: You MUST consult this skill BEFORE making any modifications to Markdown files (including, but not limited to, all files whose name ends in .md).
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: documentation
---

# Write Markdown Skill

You MUST create or modify Markdown documentation in this project according to the conventions defined below.

## Requirement Keywords

The keywords "MUST", "MUST NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 ([RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119) and [RFC 8174](https://datatracker.ietf.org/doc/html/rfc8174)).
Only uppercase usage carries these special meanings.
Lowercase usage has its normal English meaning.

## Trigger

You MUST activate this skill whenever you are creating new Markdown documentation files, modifying existing Markdown documentation, or writing documentation for code, features, or processes.

## Mandatory Style Rules

Apply these rules to every Markdown file you create or modify:

### Headings

- Use ATX headings (`#` symbols) only.
- Do not use setext headings (underlined with `===` or `---`).
- Use `#` for the main title, `##` for sections, `###` for subsections, and so on.

### Code Blocks

- Use fenced code blocks with language identifiers only.
- Do not use indented code blocks.

### Sentences

- Write one sentence per line outside of code blocks.
- Sentences MUST NOT break across lines.
- Lines MUST NOT contain more than one sentence.

### Lists

- Preserve existing bullet list markers; bullets MUST be followed by exactly 1 space.
- List items can contain one or more sentences.
- When a list item is preceded by a brief title, separate the title from the rest *by `:`* (e.g., `Item title: This is the detail`).
- If a list item contains multiple sentences, each MUST be on a separate line and indented accordingly.
- Do not use other separator characters between the title and detail.

### Whitespace

- A line MUST NOT end in trailing whitespace.

### File Ending

- Every file MUST end with a newline character.

### Footnotes

- Preserve indentation of multi-line footnotes.

## Mandatory Content Requirements

- All documentation MUST follow the project's existing structure and tone.
- Use consistent terminology with existing documentation.
- All links MUST be properly formatted and functional.
- All commands and examples MUST be tested and working.
- Technical documentation MUST be kept up-to-date with code changes.

## What to Write

- Clear, concise, accurate prose.
- Active voice (not passive).
- Relevant examples and code snippets.
- References to existing documentation where appropriate.

## Verification

Before returning a Markdown file, confirm:

- All headings are ATX style with correct hierarchy
- All code blocks have language identifiers
- One sentence per line (outside code blocks)
- List markers follow the exact-1-space rule
- No trailing whitespace on any line
- The file ends with a newline
- Footnotes preserve indentation
- All links are functional
- The document structure matches project conventions
