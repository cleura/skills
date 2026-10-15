---
name: insert-links
description: >-
  Insert inline links into text while preserving the semantic context and structure of the markup language being processed.
  This skill is mandatory for every request to add links, references, citations, or annotations to text.
  **IMPORTANT**: You MUST consult this skill BEFORE editing text for link insertion.
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: documentation
---

# Insert Links Skill

You MUST insert inline links into text while preserving the semantic context and structure of the markup language being processed.

## Requirement Keywords

The keywords "MUST", "MUST NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 ([RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119) and [RFC 8174](https://datatracker.ietf.org/doc/html/rfc8174)).
Only uppercase usage carries these special meanings.
Lowercase usage has its normal English meaning.

## Trigger

You MUST activate this skill whenever the user asks you to add links, references, citations, or annotations to text, or when you are editing any markup language that supports hyperlinks (Markdown, HTML, reStructuredText, AsciiDoc, etc.).

## Mandatory Steps

Follow these steps in order:

1. **Identify linkable content**: Scan the text for key concepts, technical terms, named persons, organizations, places, events, and established ideas that would benefit from external reference.

2. **Choose a source**: Select the most specific and authoritative source available.
   Use the following priority order:
   - For established general-knowledge topics: Wikipedia
   - For technical terms: official documentation or specification pages
   - For persons: Wikipedia (if the person is notable)
   - For organizations, institutions, or events: the most authoritative available source
   - For events: a government, academic, or major news source

3. **Fetch the URL**: Use the fetch tool to retrieve the target URL.
   Confirm the response returns a successful HTTP status code (2xx) and the content loads correctly.
   If the fetch fails, try an alternative source.
   If no valid source exists, do not insert a link.
   Never insert a link that has not been verified.

4. **Insert the link**: Replace the concept, term, or person with an inline link using the markup language's link syntax.
   Examples:

   ```markdown
   [Python](https://www.python.org/) is a programming language.
   ```

   ```html
   <a href="https://www.python.org/">Python</a> is a programming language.
   ```

   ```rst
   :doc:`Python <python>` is a programming language.
   ```

5. **Verify markup integrity**: Confirm that no existing markup syntax, formatting, structure, code blocks, or other elements were altered beyond adding the link.

## What NOT to Link

- Common words or phrases that lack encyclopedic significance
- Links you cannot fetch and verify
- Links that point to generic pages when a more specific page exists

## Markup Preservation

You MUST NOT alter markup syntax when editing text.
Keep all tags, attributes, formatting markers, and structure intact.
Only edit the human-readable text content between or within markup elements.

You MUST preserve all semantic meaning: existing links, references, code, lists, tables, and other structured elements MUST remain functionally identical.
You MUST NOT change code blocks, inline code, or other literal content.
You MUST NOT change document structure: headings, sections, and hierarchy.
You MUST retain all special characters, escape sequences, and formatting required by the markup language.

## Verification

Before returning the edited text, confirm:

- Every inserted link has been fetched and verified as accessible
- Link text accurately describes the target page
- No existing links or content have been broken
- The markup remains valid after insertion
- Link choices follow the source priority order above
- Link choices are consistent with the document's tone and audience
