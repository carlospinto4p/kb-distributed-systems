---
title: "Spanner: Google's Globally-Distributed Database (abstract page)"
type: source
status: draft
tags: [transactions, consistency]
created: 2026-11-06
updated: 2026-11-06
url: https://research.google/pubs/spanner-googles-globally-distributed-database-2/
publisher: Google Research (OSDI 2012)
author: James C. Corbett, Jeffrey Dean, Michael Epstein, and 23 co-authors
published: 2012
read: 2026-11-06
---

# Spanner: Google's Globally-Distributed Database (abstract page)

## Summary

Only the publication page was read, which holds the abstract and the author
list. The abstract describes Spanner as a multi-version database that spans
the globe and replicates data synchronously, and says it is the first system
to support externally consistent distributed transactions at global scale. It
credits a time API that exposes clock uncertainty for this.

## Key passages

- "Spanner is Google's scalable, multi-version, globally-distributed, and
  synchronously-replicated database." (Abstract)
- "It is the first system to distribute data at global scale and support
  externally-consistent distributed transactions." (Abstract)
- "a novel time API that exposes clock uncertainty" (Abstract)
- "This API and its implementation are critical to supporting external
  consistency and a variety of powerful features" (Abstract)

## Used in

- [[spanner]]
- [[consistency-models]]

## Reliability

The abstract is the authors' own claim; "first" is theirs and was not
checked. The body of the paper was not read, so nothing in this knowledge
base describes how the time API or the transactions work. The full paper is
linked from the page and is the next thing to ingest.
