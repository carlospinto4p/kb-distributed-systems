---
title: "CAP Twelve Years Later: How the Rules Have Changed"
type: source
status: draft
tags: [cap, consistency, availability]
created: 2026-11-06
updated: 2026-11-06
url: https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed/
publisher: InfoQ, from IEEE Computer
author: Eric Brewer
published: 2012-05-30
read: 2026-11-06
---

# CAP Twelve Years Later: How the Rules Have Changed

## Summary

Brewer, who proposed the CAP idea, argues that "pick two of three" is
misleading. Partitions are rare, so a system can offer both consistency and
availability most of the time, and designers should decide in advance what to
do while a partition lasts and how to recover afterwards. The article says it
first appeared in Computer magazine.

## Key passages

- "The CAP theorem asserts that any networked shared-data system can have
  only two of three desirable properties." (Introduction)
- "CAP prohibits only a tiny part of the design space" (Why "2 of 3" is
  misleading)
- The strategy has three steps: "detect partitions, enter an explicit
  partition mode" and then recover (same section)
- "Thus, pragmatically, a partition is a time bound on communication."
  (CAP-latency connection)
- "if the system requires ACID isolation, it can operate on at most one side
  during a partition" (ACID, BASE and CAP)

## Used in

- [[cap-theorem]]
- [[when-is-strong-consistency-worth-it]]
- [[how-do-crdts-converge]]

## Reliability

Written by the person who proposed CAP, so it is an authoritative account of
what he meant and a poor place to check the formal proof. The page's text was
read in full for the first 40,000 of 61,000 characters; the remainder (the
compensating-transactions discussion) was only available as a summary and is
not used in any note.
