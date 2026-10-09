---
name: six-rules
description: >-
  Edit text following the Remedy of Six Rules, preserving all semantic context of the markup language being processed.
  Use this skill whenever the user asks to edit, revise, simplify, or improve writing in any markup language (Markdown, HTML, reStructuredText, etc.).
  **IMPORTANT**: This skill MUST be consulted BEFORE editing any text content.
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: writing
---

# Apply the Remedy of Six Rules

This skill provides instructions for editing text to be clear, direct, and plain, while fully preserving the semantic context and structure of whatever markup language is being processed.

## When to use this skill

Use this skill when:

- The user asks to edit, revise, simplify, or improve writing
- The user wants text to be more concise or plain-spoken
- Writing in any markup language (Markdown, HTML, reStructuredText, AsciiDoc, etc.)

## The Six Rules

These rules are drawn from George Orwell's essay "Politics and the English Language" (1946).
Apply them to all text editing:

1. Never use a metaphor, simile, or other figure of speech which you are used to seeing in print.
2. Never use a long word where a short one will do.
3. If it is possible to cut a word out, always cut it out.
4. Never use the passive where you can use the active.
5. Never use a foreign phrase, a scientific word, or a jargon word if you can think of an everyday English equivalent.
6. Break any of these rules sooner than say anything outright barbarous.

## Markup Preservation

When editing text inside markup:

- **Do not alter** markup syntax: keep all tags, attributes, formatting markers, and structure intact
- **Only edit** the human-readable text content between or within markup elements
- **Preserve** all semantic meaning: links, references, code, lists, tables, and other structured elements must remain functionally identical
- **Keep** code blocks, inline code, and other literal content untouched
- **Maintain** document structure: headings, sections, and hierarchy must not change
- **Retain** all special characters, escape sequences, and formatting required by the markup language

## Editing Principles

- Prefer short, direct sentences
- Use active voice wherever possible
- Replace verbose phrases with simpler alternatives
- Remove filler words and redundant expressions
- Choose familiar words over obscure or technical ones
- Never sacrifice clarity or introduce awkwardness just to follow a rule -- rule six overrides all others
