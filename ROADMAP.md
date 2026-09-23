# Roadmap Authoring Standard

This is the required specification for content in `roadmaps/`. A roadmap is a
prerequisite-ordered curriculum of compact, self-contained lessons. It must take
a learner from the technology's foundations to practical production use.

## 1. Required deliverables

Publish every roadmap in English (`en`), neutral Spanish (`es`), and Brazilian
Portuguese (`pt`) with this exact layout:

```text
roadmaps/<slug>/
├── en/
│   ├── roadmap.json
│   └── sections/<section-id>/<topic-id>.md
├── es/
│   ├── roadmap.json
│   └── sections/<section-id>/<topic-id>.md
└── pt/
    ├── roadmap.json
    └── sections/<section-id>/<topic-id>.md
```

Every declared topic must have exactly one lesson at its corresponding path. Do
not add undeclared lessons or omit declared lessons.

## 2. Research policy

Research the subject before designing the curriculum. Do not rely exclusively
on prior knowledge for facts that may have changed.

1. Confirm the current stable release, supported environments, active APIs,
   recommended workflows, and known deprecations.
2. Build coverage from primary sources: official documentation,
   specifications, canonical repositories, release notes, and migration guides.
3. Use MDN or a reputable tutorial only when it improves explanation or fills a
   teaching gap.
4. Exclude obsolete practices unless a lesson explicitly covers migration or
   legacy maintenance.
5. Treat prerelease features as optional context and label their status clearly.
6. Verify every URL and version claim before delivery.

Prefer one authoritative source over repetitive secondary sources. Never invent
APIs, commands, configuration, compatibility claims, or citations.

## 3. Curriculum design

Order sections by prerequisite dependency and topics by practical learning
sequence. Include only areas relevant to the technology, but explicitly assess:

- mental model, runtime, and project setup;
- core syntax, data model, or component model;
- everyday workflows and composition;
- state, data, I/O, or persistence where applicable;
- errors, debugging, and observability;
- testing and quality practices;
- security and accessibility where applicable;
- performance and resource management;
- interoperability, packaging, and deployment;
- upgrades, compatibility, and production operation.

A topic is one lesson-sized concept or workflow. Group APIs normally learned and
used together. Do not create a topic for every method, property, flag, or minor
API. Do not combine unrelated concepts merely to reduce the topic count.

There is no mandatory section or topic count. Completeness, useful granularity,
and prerequisite order determine acceptance.

## 4. Localization

Approve the English curriculum first, then localize it.

- Use natural technical English, neutral Spanish, and Brazilian Portuguese.
- Translate titles, descriptions, explanations, and reference labels when
  appropriate.
- Keep the slug, IDs, orders, reference URLs, API names, commands, filenames,
  code, and identifiers identical across locales.
- Keep the exact same section and topic tree in every locale.
- Preserve established technical terms instead of forcing literal translations.
- Localize code comments only when behavior and cross-locale comparability remain
  unchanged.

## 5. Roadmap manifest

Every locale requires a `roadmap.json` with this structure:

```json
{
  "locale": "en",
  "status": "published",
  "title": "Technology",
  "slug": "technology",
  "description": "A prerequisite-ordered learning path for Technology.",
  "metadata": {
    "tags": ["technology", "programming"]
  },
  "sections": [
    {
      "id": "foundations",
      "title": "Foundations",
      "order": 1,
      "topics": [
        {
          "id": "core-mental-model",
          "title": "Core Mental Model",
          "order": 1,
          "references": [
            {
              "label": "Official documentation: Core concepts",
              "url": "https://example.com/docs/core-concepts"
            },
            {
              "label": "Official guide: Getting started",
              "url": "https://example.com/docs/getting-started"
            }
          ]
        }
      ]
    }
  ]
}
```

### Top-level fields

| Field | Requirement |
| --- | --- |
| `locale` | Must match the directory: `en`, `es`, or `pt`. |
| `status` | Use `published` for complete, reviewed content. |
| `title` | Official technology name with correct capitalization. |
| `slug` | Stable English `kebab-case`; identical in every locale. |
| `description` | One concise sentence defining scope and progression. |
| `metadata.tags` | Focused discovery tags; identical in every locale. |
| `sections` | Prerequisite-ordered curriculum sections. |

### Section and topic fields

- Section and topic IDs must be English `kebab-case`.
- Section IDs must be unique within the roadmap.
- Topic IDs must be unique across the entire roadmap.
- Every `order` sequence starts at 1, increases by 1, and has no gaps or
  duplicates.
- Titles must be specific, instructional, and localized.
- Every topic contains one or two references.
- The first reference should be official or primary whenever possible.
- References belong only in `roadmap.json`; lessons must not contain citations,
  source lists, or external links.

## 6. Lesson format

Save every lesson as `sections/<section-id>/<topic-id>.md` and use this shape:

````markdown
# Exact Localized Topic Title

Explain the concept, its role, and when it should be used.

```language
// Small, valid, focused example
```

Explain the important behavior, tradeoff, limitation, or common mistake shown by
the example.
````

### Requirements

- The first line is one H1 exactly matching the localized manifest title.
- Do not add YAML frontmatter, additional headings, links, or references.
- Make the lesson understandable without requiring the reader to open a source.
- Explain what the concept is, why it matters, when to use it, and the minimum
  needed to apply it correctly.
- Prefer one focused example over disconnected snippets.
- Use valid syntax, real APIs, current conventions, and necessary imports or
  context.
- Explain relevant limitations, safety concerns, performance implications, or
  common mistakes.
- Keep terminology consistent with official documentation and related lessons.

### Prohibited content

- generic introductions, marketing claims, or historical filler;
- placeholders presented as working code;
- unexplained advanced APIs in foundational lessons;
- duplicated explanations already covered by prerequisites;
- obsolete syntax unless the topic explicitly covers migration or legacy code.

## 7. Acceptance checklist

### Structure and data

- All three locale directories exist.
- Every topic has exactly one matching lesson; no orphaned lessons exist.
- Paths and filenames exactly match their IDs.
- Every JSON file parses successfully.
- IDs are valid, unique `kebab-case`; orders begin at 1 with no gaps.
- Every topic has one or two valid references.
- Locale trees have identical IDs, orders, URLs, and filenames.

### Editorial quality

- Every lesson H1 exactly matches its localized manifest title.
- Lessons contain no frontmatter, additional headings, or references.
- Examples use valid syntax, real APIs, and current recommended practices.
- Coverage is complete without fragmentation into trivial API-level topics.
- All three locales read naturally and use consistent terminology.

### Technical hygiene

- No broken links, placeholders, null bytes, binary characters, or encoding
  errors remain.
- No credentials, private data, unverifiable claims, or generated artifacts are
  included.
