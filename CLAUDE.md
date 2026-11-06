# CLAUDE.md — kb-distributed-systems

## Project Overview

A small knowledge base on distributed systems: how machines that can fail
and lose messages still agree, order events and keep copies of data in step.
Every claim traces to a paper or a primary page, so the notes can be checked.

It is pure markdown, with no code and no build. **Read
`.claude/rules/knowledge-base.md` before touching any note.** It defines the
layout, the frontmatter, how to link, and the rule that every claim needs a
source or an `(unverified)` marker.

## Topics

| Folder | Holds |
|--------|-------|
| `concepts/` | Ideas: time and ordering, quorums, consistency, CAP. |
| `consensus/` | The consensus problem, its impossibility result, Paxos, Raft. |
| `systems/` | Real systems that apply the ideas: Dynamo, Spanner. |
| `questions/` | Open questions the notes cannot answer yet. |
| `sources/` | One note per external source. |
| `inbox/` | Raw captures waiting to be turned into notes. |

## Note types

`hub`, `concept`, `algorithm`, `system`, `question`, `source`.

## Project Rules

- `git pull` before any work.
- Plain commits, notes as `note: <what changed>`. No versions, no tests.
- Write a claim only from a source that was read. When a source cannot be
  read, say so in its note and in the notes that would have used it.
