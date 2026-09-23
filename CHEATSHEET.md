# Cheatsheet Authoring Standard

This is the required specification for content in `cheatsheets/`. A cheatsheet
is a fast, task-oriented reference for readers who understand the fundamentals
and need accurate, copy-ready examples. It is not a tutorial, API dump, or
condensed roadmap.

## 1. Required deliverables

Create one Markdown file per locale:

```text
cheatsheets/<slug>/
├── en.md
├── es.md
└── pt.md
```

All locales must cover the same major areas in the same order. Do not add or
remove material in only one locale.

## 2. Research policy

Verify syntax, commands, APIs, configuration keys, and recommended workflows
before writing.

- Prioritize official documentation, specifications, canonical repositories,
  and current release notes.
- Prefer stable, broadly supported features used in everyday work.
- Clearly identify important version-specific behavior.
- Avoid deprecated APIs, unsafe shortcuts, and undocumented behavior.
- Test or otherwise validate examples when practical.

Never invent an API or simplify an example until it becomes technically false.

## 3. Localization

Write English first, then localize into neutral Spanish and Brazilian Portuguese.

- Translate titles, descriptions, groups, entry labels, and prose naturally.
- Keep the slug, status, tags, URLs, API names, commands, code, filenames, and
  identifiers consistent across locales.
- Preserve official names and established technical terms.
- Localize code comments only when technically safe and useful.

## 4. Frontmatter

Every file must begin with valid YAML frontmatter in this shape:

```yaml
---
locale: en
status: published
title: "Technology"
slug: technology
description: "A task-oriented quick reference for everyday Technology workflows."
tags:
  - technology
  - cheatsheet
  - quick-reference
references:
  - label: "Official documentation"
    url: https://example.com/docs
  - label: "Official API reference"
    url: https://example.com/api
  - label: "Official repository"
    url: https://github.com/example/project
---
```

| Field | Requirement |
| --- | --- |
| `locale` | Must match the filename: `en`, `es`, or `pt`. |
| `status` | Use `published` only for complete, reviewed content. |
| `title` | Official technology name with correct capitalization. |
| `slug` | Stable English `kebab-case`; identical across locales. |
| `description` | One sentence defining the practical purpose. |
| `tags` | Include the technology, `cheatsheet`, and `quick-reference`. |
| `references` | Exactly three reliable sources, prioritizing official material. |

Keep the slug, status, tags, and reference URLs identical across locales.
Reference labels may be localized. Do not repeat source links in the body.

## 5. Body structure

After the frontmatter, use this pattern:

````markdown
# Technology

Task-oriented quick reference. Find and copy the smallest example that matches
your current need.

## Major Workflow Area

**Specific Task or Concept**

```language
// Minimal copy-ready example
```
````

### Heading rules

- Use one H1 matching the frontmatter title.
- Add one short sentence explaining the page's purpose.
- Use H2 headings for major workflow or feature groups.
- Use bold labels for individual entries.
- Avoid deeper headings unless genuinely required.
- Keep group and entry order aligned across locales.

### Coverage rules

Prioritize high-frequency operations:

- project setup and essential commands;
- core syntax and everyday patterns;
- common composition and integration tasks;
- configuration and environment handling;
- errors, debugging, and testing;
- safe defaults, security, and performance where relevant;
- build, packaging, deployment, and maintenance workflows.

Not every roadmap topic belongs in a cheatsheet. Include a topic only when a
concise example helps someone perform or recall a task.

## 6. Example quality

Every example must be:

- minimal without omitting context required for correctness;
- syntactically valid with the correct fence language;
- based on real, stable APIs and current practices;
- safe to copy in the context described by its label;
- focused on one task and distinct from nearby examples;
- understandable without a long prose explanation.

Include imports, configuration keys, paths, or command context when needed. Use
recognizable placeholders such as `DATABASE_URL` or `example.com`; never include
credentials, private URLs, or sensitive values.

Do not include:

- long tutorial paragraphs or exhaustive API inventories;
- output that cannot be produced by the shown code or command;
- ellipses that hide essential logic;
- experimental syntax presented as the stable default;
- duplicate entries that differ only cosmetically.

## 7. Acceptance checklist

### Structure and metadata

- `en.md`, `es.md`, and `pt.md` exist in the correct directory.
- Frontmatter parses and contains every required field.
- Each locale contains exactly three references.
- Invariant fields and reference URLs match across locales.

### Content quality

- The H1 matches the frontmatter title.
- Major groups and entries appear in the same order in every locale.
- Examples are concise, useful, non-duplicative, and copy-ready.
- Syntax, commands, imports, and APIs are correct and current.
- Technical terminology and translations are consistent.

### Technical hygiene

- Code fences are balanced and use appropriate language identifiers.
- Links resolve to the intended authoritative pages.
- No metadata placeholders, credentials, private data, null bytes, binary
  characters, or encoding errors remain.
