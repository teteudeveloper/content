# Codex Authoring Standard

This is the required specification for content in `codex/`. A Codex entry is a
concise, structured identity record for a technology. It supports discovery and
provides verified facts, official links, and consistent branding. It is not a
tutorial, roadmap, release history, or marketing profile.

## 1. Required deliverables

Create one JSON document per locale:

```text
codex/<slug>/
├── en/codex.json
├── es/codex.json
└── pt/codex.json
```

All documents must describe the same entity and share the same invariant fields.

## 2. Research policy

Confirm every factual value using authoritative sources.

1. Identify the official project or product website.
2. Identify the canonical source repository, not a mirror or community fork.
3. Verify the official name, capitalization, maintainer, license, primary
   language, platform, runtime, and focus where applicable.
4. Confirm the official brand color and expected logo asset.
5. Avoid volatile facts such as download counts and popularity rankings.
6. Include a version only when essential, current, and maintained by the content
   update process.

Do not infer a license, maintainer, or repository from third-party pages when a
primary source exists. Never invent missing metadata.

## 3. Localization

Write English first, then localize into neutral Spanish and Brazilian Portuguese.

These fields must remain identical:

- `slug` and `status`;
- `tags`;
- `branding.color` and `branding.logo`;
- `links.official` and `links.repository`.

Localize `description`, metadata labels, and descriptive metadata values when
appropriate. Preserve official product names, organization names, licenses,
programming language names, and technical identifiers.

## 4. Schema

Every `codex.json` must follow this structure:

```json
{
  "locale": "en",
  "title": "Technology",
  "slug": "technology",
  "description": "A concise factual description of the technology and its primary purpose.",
  "status": "published",
  "tags": ["technology", "programming"],
  "branding": {
    "color": "#000000",
    "logo": "/logos/technology.svg"
  },
  "links": {
    "official": "https://example.com",
    "repository": "https://github.com/example/project"
  },
  "metadata": [
    {
      "label": "Maintainer",
      "value": "Project Team"
    },
    {
      "label": "License",
      "value": "MIT"
    },
    {
      "label": "Platform",
      "value": "Web"
    },
    {
      "label": "Focus",
      "value": "Application development"
    }
  ]
}
```

## 5. Field requirements

| Field | Requirement |
| --- | --- |
| `locale` | Must match the parent directory: `en`, `es`, or `pt`. |
| `title` | Official name and capitalization; normally unchanged by locale. |
| `slug` | Stable English `kebab-case`; identical across locales. |
| `description` | One neutral sentence describing type, purpose, and focus. |
| `status` | Use `published` only for complete, verified entries. |
| `tags` | Focused discovery terms; identical across locales. |
| `branding.color` | Verified official or primary six-digit hexadecimal color. |
| `branding.logo` | Application asset path using `/logos/<slug>.svg`. |
| `links.official` | Canonical HTTPS website or documentation entry point. |
| `links.repository` | Canonical upstream source repository. |
| `metadata` | Four or five stable, useful label/value facts. |

## 6. Editorial requirements

### Description

- State what the technology is and its primary purpose.
- Use concise, neutral, factual language.
- Avoid “best,” “fastest,” “most popular,” and similar promotional claims.
- Do not turn the description into setup instructions or a feature inventory.

### Tags

- Use lowercase English discovery terms.
- Include the technology slug when appropriate.
- Prefer precise categories such as `database`, `web-framework`, or
  `programming-language` over vague promotional terms.
- Do not localize tags.

### Branding

- Use a documented official color where available.
- Use uppercase six-digit hexadecimal notation for consistency.
- Confirm that `/logos/<slug>.svg` exists in the consuming application.
- If absent, report the dependency explicitly; never use an unrelated or
  temporary logo silently.

### Links

- Use canonical HTTPS URLs without tracking parameters.
- Point `official` to the official website or documentation home.
- Point `repository` to the canonical upstream repository.
- Do not use search results, mirrors, aggregators, or registry pages when the
  canonical repository is known.

### Metadata

Choose four or five fields useful for identifying the technology. Suitable
examples include maintainer, language, license, runtime, platform, type,
rendering model, or primary focus. Choose fields relevant to the entity instead
of forcing the same labels on every technology.

Metadata must be stable, verifiable, concise, and non-promotional. Avoid current
version, release date, popularity, stars, downloads, or market share unless the
product explicitly requires and maintains those values.

## 7. Acceptance checklist

### Structure and schema

- English, Spanish, and Portuguese files exist at the required paths.
- Every file parses as valid JSON with the required fields and value types.
- Each entry contains four or five metadata items.

### Cross-locale consistency

- Slug, status, tags, branding, and URLs are identical across locales.
- Descriptions and textual metadata are naturally localized.
- Official names, licenses, and identifiers remain unchanged.

### Fact checking and hygiene

- Official and repository URLs are canonical and reachable.
- Metadata facts are supported by authoritative sources.
- Brand color and logo path are correct.
- Descriptions contain no unsupported or promotional claims.
- No example values, credentials, private data, null bytes, binary characters,
  malformed Unicode, or encoding errors remain.
