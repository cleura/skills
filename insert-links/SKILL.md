---
name: insert-links
description: >-
  Edit text in markup languages that support hyperlinks by replacing mentions of key concepts, terms, and
  persons with inline links to Wikipedia pages or other authoritative sources. Every link must be fetched
  at insertion time to confirm it is available. Use this skill whenever the user asks to add links,
  reference, cite, or annotate text.
  **IMPORTANT**: This skill MUST be consulted BEFORE editing text for link insertion.
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: documentation
---

# Insert Links Skill

This skill provides instructions for inserting inline links into text while preserving the semantic context and structure of the markup language being processed.

## When to use this skill

Use this skill when:

- The user asks to add links, references, citations, or annotations to text
- The user wants to link key concepts, terms, or persons to external sources
- Editing any markup language that supports hyperlinks (Markdown, HTML, reStructuredText, AsciiDoc, etc.)

## Core Instructions

When editing text:

1. **Identify linkable content**: Look for mentions of key concepts, technical terms, named persons, organizations, places, events, and established ideas that would benefit from external reference.

2. **Choose authoritative sources**: Prefer Wikipedia pages for general knowledge topics.
   Use other authoritative sources (official documentation, academic institutions, government publications, reputable news organizations) when they are more appropriate or reliable.

3. **Fetch every link before inserting**: Before adding any link, fetch the target URL to confirm it is accessible and returns a valid response.
   Never insert a link that has not been verified.

4. **Replace text with inline links**: Convert the mentioned concept, term, or person into an inline link using the markup language's link syntax (e.g., `[text](url)` in Markdown, `<a href="url">text</a>` in HTML).

5. **Preserve markup context**: Keep all existing markup intact.
   Do not alter formatting, structure, code blocks, or other elements beyond adding the link.

## Link Selection Guidelines

- Prefer the most specific and relevant Wikipedia article over a generic one
- When a concept has a well-known Wikipedia page, use it
- For technical terms, official documentation or specification pages may be more appropriate
- For persons, use their Wikipedia page if available and notable
- For organizations, institutions, or events, use the most authoritative available source
- Do not link common words or phrases that lack encyclopedic significance

## Fetch Verification

For every link to be inserted:

1. Use the fetch tool to retrieve the target URL
2. Confirm the response is a successful HTTP status code (2xx)
3. Confirm the content loads correctly
4. Only insert the link after successful verification
5. If a link fails to fetch, try an alternative source or omit the link rather than leaving a broken reference

## Markup Preservation

When editing text inside markup:

- **Do not alter** markup syntax: keep all tags, attributes, formatting markers, and structure intact
- **Only edit** the human-readable text content between or within markup elements
- **Preserve** all semantic meaning: existing links, references, code, lists, tables, and other structured elements must remain functionally identical
- **Keep** code blocks, inline code, and other literal content untouched
- **Maintain** document structure: headings, sections, and hierarchy must not change
- **Retain** all special characters, escape sequences, and formatting required by the markup language

## Link Format Examples

Markdown:

```markdown
[Python](https://www.python.org/) is a programming language.
```

HTML:

```html
<a href="https://www.python.org/">Python</a> is a programming language.
```

reStructuredText:

```rst
:doc:`Python <python>` is a programming language.
```

## Quality Checks

Before completing link insertion:

- Every inserted link has been fetched and verified as accessible
- Link text accurately describes the target page
- No existing links or content have been broken
- The markup remains valid after insertion
- Link choices are consistent with the document's tone and audience
