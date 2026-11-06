# Knowledge Base Conventions

This repository is a knowledge base. Its markdown notes are the product:
there is no application here, and nothing is generated from anything else.
A person and an LLM both read and write the notes, so every convention below
exists to keep them findable, linkable and honest about what is known.

## Layout

| Path | Holds |
|------|-------|
| `index.md` | The entry point. Links to every topic hub. |
| `<topic>/<topic>.md` | The hub note for a topic folder. Links to its notes. |
| `<topic>/*.md` | One note per idea, algorithm, system or question. |
| `sources/` | One note per external source (paper, article, page). |
| `inbox/` | Raw captures not yet processed into notes. |
| `templates/` | Note templates. Not notes: never linked, never checked. |

Topic folders are listed in `CLAUDE.md`.

## File names are note identities

- **kebab-case, unique across the whole repository.** `[[quorum]]` must
  resolve to exactly one file, whichever folder it lives in.
- Source notes start with `src-` (`src-raft-paper.md`).
- Renaming a note means updating every link to it in the same change.

## Frontmatter

Every note starts with this block:

```yaml
---
title: Plain-language title
type: concept         # the allowed types are listed in CLAUDE.md
status: draft         # draft | reviewed | outdated
tags: [consensus]
created: 2026-11-06
updated: 2026-11-06
---
```

- `draft` means written, not yet checked. `reviewed` means a person read it
  and agrees. `outdated` means kept for history, superseded by a linked note.
- `question` notes also use `status`; an answered question is `reviewed`
  and its answer section is filled in.
- Update `updated` whenever the body changes. Dates are ISO. A source's
  `published` may be just a year or a year and month when the page gives no
  more.

## Links

- Link notes with `[[file-name]]` or `[[file-name|text shown]]`.
- Every note links to its hub, and its hub links back. A note nothing links
  to is an orphan.
- Prefer a link to an existing note over repeating its content.
- Plain markdown links are for external URLs only.

## Facts and claims

This is the rule that matters most. A knowledge base full of confident
claims nobody checked is worse than an empty one, because it looks finished.

Any claim about the world outside this repository (what a paper proves, what
a system does, when something was published) takes exactly one of:

1. **A source link**: `[[src-some-paper]]`, pointing at a source note that
   records the URL, the publisher, the publication date and the date it was
   read.
2. **An inline citation**: `([publisher](https://…), checked 2026-11-06)`.
3. **The marker `(unverified)`** right after the claim, when it was written
   from memory or from a source that could not be read.

Never write a claim with none of the three. Quote a source's own words when
the exact wording matters, and keep quotes short.

Opinions, plans and hypotheses are fine without sources, but say that they
are one: "Hypothesis: …", "My guess: …".

## Working on notes

- **Search before creating.** Grep for the topic first; extend an existing
  note rather than writing a near-duplicate.
- **One idea per note.** When a note covers two things, split it and link
  the halves.
- **Record the gap.** When a question cannot be answered from the notes,
  write it down as a `question` note in the right topic instead of answering
  from general knowledge.

## Commits

Plain descriptive commits. Note changes are committed as
`note: <what changed>`. There is no version, no changelog and no test suite:
git history is the record.
