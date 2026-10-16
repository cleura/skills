---
name: translate
description: >-
  Translate content into a different natural language while preserving all markup.
  This skill is mandatory for every content translation task.
  **IMPORTANT**: You MUST consult this skill BEFORE translating any content.
license: MIT
compatibility: opencode
metadata:
  audience: developers
  workflow: documentation
---

# Translate Skill

You MUST translate content into a target natural language while preserving all markup syntax and structure.

## Requirement Keywords

The keywords "MUST", "MUST NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in BCP 14 ([RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119) and [RFC 8174](https://datatracker.ietf.org/doc/html/rfc8174)).
Only uppercase usage carries these special meanings.
Lowercase usage has its normal English meaning.

## Trigger

You MUST activate this skill whenever the user asks you to translate content into another natural language, or when you are generating a localized version of a document.

## Target Language

1. If the user specifies a target language, use that language.
2. If the user does NOT specify a target language, you MUST target the agent's currently configured UI language.
3. When the user refers to a language by code (e.g., `en`, `ja`, `zh-CN`), resolve it to the full language name before proceeding.
4. If the target language cannot be determined, you MUST ask the user to specify one before proceeding.

If the target language features a T-V distinction, you MUST ask the user whether the translation should use the familiar (informal) or the polite (formal) form of addressing the reader.

## Source File Protection

You MUST NOT overwrite, modify, delete, or otherwise alter any source language file.
Translation MUST produce a new file (or update an existing target-language file) in the appropriate output location.
You MUST NOT modify the original source file under any circumstances.

You MAY overwrite or amend pre-existing translations in the target language file, provided the source file remains untouched.

## Markup Preservation

You MUST NOT alter any markup syntax, formatting, structure, code, or literal content.

You MUST preserve all of the following in their entirety:

- All markup tags, attributes, and closing markers
- All code blocks and inline code
- All links, references, citations, and footnotes (including their URIs and anchors)
- All lists, tables, headings, and document hierarchy
- All special characters, escape sequences, and formatting markers
- All front matter, metadata blocks, and configuration directives
- All image sources, alt text attributes, and embed syntax

You MUST ONLY translate human-readable text content that appears between or within markup elements.

## Technical Terms

Technical terms are domain-specific identifiers, proper nouns of software projects, APIs, libraries, protocols, file formats, command names, configuration keys, and standardized acronyms that have a generally accepted treatment in the target language.

For every technical term you encounter during translation:

1. **Check** whether the target language has a generally accepted translation for that term.
   Consult authoritative resources such as official documentation in the target language, established glossaries, or widely used community translations.
2. **If a generally accepted translation exists**, retain the original language form.
   You MAY append the translated form in parentheses immediately after the original term on first use, if that addition improves clarity for the target audience.
3. **If the word is a loanword in the target language,** use the loanword and follow capitalisation rules.
   (For example, when translating from English to German, `computer` becomes `Computer`.
   When translating from German to English, `Sauerkraut` becomes `sauerkraut`.)
4. **If no generally accepted translation exists**, retain the original language form unchanged.
5. **If the term is purely descriptive** (not a technical identifier), translate it naturally into the target language.

Examples of terms to retain in the original language:

- Software project names: `Git`, `Python`, `Docker`, `Kubernetes`
- API and library names: `REST`, `GraphQL`, `TensorFlow`, `PyTorch`
- Protocol and format names: `HTTP`, `JSON`, `YAML`, `HTML`
- Command names: `git commit`, `npm install`, `kubectl apply`
- Configuration keys and variable names: `config.yaml`, `DATABASE_URL`, `MAX_RETRIES`
- Standardized acronyms: `API`, `URI`, `HTTP`, `CSS`, `SQL`

## Mandatory Steps

Follow these steps in order:

1. **Determine the target language**: Identify the target language per the Target Language section above.
2. **Identify the source file and its language**: Determine the source language and the file path.
3. **Determine the output file path**: Derive the target-language file path from the source file path, using the project's existing localization conventions if present.
   If no convention exists, place the translated file adjacent to the source file with a language suffix in the file name (e.g., `README.ja.md` for Japanese).
4. **Scan for technical terms**: Identify every technical term in the source text.
   Check whether the target language has a generally accepted translation for each one.
   Record which terms MUST be retained in the original language.
5. **Translate only human-readable text**: Translate the human-readable content while preserving all markup exactly as it appears in the source.
   Retain every technical term in the original language as determined in Step 4.
6. **Write the target file**: Write the translated content to the output file determined in Step 3.
   You MAY overwrite or amend an existing target-language file, but you MUST NOT modify the source file.
7. **Verify markup integrity**: Confirm that no markup syntax, formatting, structure, code blocks, links, references, or other elements were altered beyond translating the human-readable text.

## Verification

Before returning the translated content, confirm:

- The target language is correct and matches the user's request or the agent's configured UI language
- The source file has not been modified in any way
- The target-language file has been written or amended correctly
- All markup syntax is intact: tags, attributes, formatting markers, code blocks, links, references, lists, tables, headings, and hierarchy
- All technical terms with a generally accepted translation in the target language are retained in the original language
- All other technical terms are retained in the original language
- All human-readable text outside markup has been translated to the target language
- The translation is fluent and idiomatic in the target language
