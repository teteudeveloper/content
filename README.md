# DevHub 404 Content

Repository-driven content for the DevHub 404 ecosystem. The application
consumes this repository as the `content` Git submodule; it is not application
code and should be changed in this repository before the application updates
the submodule reference.

## Content collections

| Collection | Purpose |
| --- | --- |
| `cheatsheets/` | Concise references organized by technical topic |
| `codex/` | Structured entries for technologies and concepts |
| `roadmaps/` | Prerequisite-ordered curricula with compact lessons |

There is intentionally no `tools/` collection in this repository. DevHub
Tools are executable product capabilities and will be implemented directly in
the main DevHub application, together with a coherent interface. Tool changes
are not accepted as content contributions here for now.

The consuming application loads these collections as Astro content. The
corresponding schemas and rendering integration live in the application's
`apps/client/src/content.config.ts` and client features.

## Content standards

Every new or updated entry must comply with the authoring standard for its
collection. A contribution is incomplete until its standard's acceptance
checklist passes.

| Collection | Required standard | Covers |
| --- | --- | --- |
| Roadmaps | [ROADMAP.md](./ROADMAP.md) | Research, curriculum design, manifests, lessons, localization, and validation |
| Cheatsheets | [CHEATSHEET.md](./CHEATSHEET.md) | Frontmatter, task-oriented organization, examples, localization, and validation |
| Codex | [CODEX.md](./CODEX.md) | Verified metadata, branding, canonical links, localization, and validation |

## Writing content

- Provide English, neutral Spanish, and Brazilian Portuguese versions.
- Keep one subject or learning path per file.
- Prefer precise explanations, practical examples, and links to authoritative
  sources.
- Keep JSON, YAML frontmatter, paths, and localized variants consistent with the
  applicable authoring standard.
- Do not add credentials, private data, or unverifiable claims.
- Update an existing entry instead of creating a duplicate.

Content is educational and repository-driven. It is separate from user-authored
Articles, Questions, Answers, Projects, and other content published through
the platform. Tools are also separate: they belong to the application's
implementation and product interface, not to this repository's content
collections.

## Contribution workflow

Changes to Cheatsheets, Codex and Roadmaps are made in this repository and
reviewed here first:

```bash
git switch -c docs/short-description
# edit the Markdown content
git add .
git commit -m "docs(content): update entry"
git push -u origin docs/short-description
```

After the content change is accepted, update the submodule reference in the
application repository:

```bash
cd ../app
git add content
git commit -m "chore(content): update content submodule"
```

The application PR must point to the accepted content commit. Do not edit a
second copy under `app/apps/client/src/content`; the submodule is the source
of truth once the integration is in place.

## Verification

Run the application checks from the app repository:

```bash
cd ../app
pnpm check
pnpm build
```

These checks validate content metadata, collection schemas, and rendering
integration.
