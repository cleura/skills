---
name: six-rules
description: >-
  Edit text following the Remedy of Six Rules, preserving all semantic context of the markup language being processed.
  This skill is mandatory for every text-editing task.
  **IMPORTANT**: You MUST apply all six rules to every piece of text you edit.
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: writing
---

# Apply the Remedy of Six Rules

You MUST edit all text to be clear, direct, and plain while fully preserving the semantic context and structure of whatever markup language is being processed.

## Requirement Keywords

The keywords "MUST", "MUST NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 ([RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119) and [RFC 8174](https://datatracker.ietf.org/doc/html/rfc8174)).
Only uppercase usage carries these special meanings.
Lowercase usage has its normal English meaning.

## Trigger

You MUST activate this skill whenever the user asks you to edit, revise, simplify, or improve writing in any markup language (Markdown, HTML, reStructuredText, AsciiDoc, etc.).

## The Six Rules

These rules come from George Orwell's essay "Politics and the English Language" (1946).
Apply them to every piece of text you edit:

1. Never use a metaphor, simile, or other figure of speech which you are used to seeing in print.
2. Never use a long word where a short one will do.
3. If it is possible to cut a word out, always cut it out.
4. Never use the passive where you can use the active.
5. Never use a foreign phrase, a scientific word, or a jargon word if you can think of an everyday English equivalent.
6. Break any of these rules sooner than say anything outright barbarous.

Rule 6 overrides all others when a conflict arises.

## Markup Preservation

You MUST NOT alter markup syntax when editing text.
Keep all tags, attributes, formatting markers, and structure intact.
Only edit the human-readable text content between or within markup elements.

You MUST preserve all semantic meaning: links, references, code, lists, tables, and other structured elements MUST remain functionally identical.
You MUST NOT change code blocks, inline code, or other literal content.
You MUST NOT change document structure: headings, sections, and hierarchy.
You MUST retain all special characters, escape sequences, and formatting required by the markup language.

## Mandatory Editing Steps

1. Read the entire piece of text before making any changes.
2. Apply all six rules to every sentence.
3. Remove every word that does not carry meaning.
4. Convert every passive construction you can into active voice.
5. Replace every jargon, foreign phrase, and obscure term with its everyday English equivalent.
6. Verify that the edited text preserves the original meaning.
7. Verify that no markup syntax was altered.

## What to Remove

- Metaphors and similes that are clichéd
- Any word that can be cut without losing meaning
- Passive voice constructions
- Jargon, scientific terminology, and foreign phrases
- Filler words and redundant expressions

## What to Use Instead

- Short, direct sentences
- Active voice
- Familiar, everyday English words
- Simple alternatives to complex terms

## Verification

Before returning edited text, confirm:

- Every sentence uses active voice unless passive is the only clear option
- No clichéd metaphors or similes remain
- Every word carries meaning; no filler words exist
- No jargon, foreign phrases, or obscure terms are used
- Markup syntax is unchanged
- The original meaning is fully preserved
