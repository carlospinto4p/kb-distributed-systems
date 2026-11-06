---
title: CAP theorem
type: concept
status: draft
tags: [cap, consistency, availability]
created: 2026-11-06
updated: 2026-11-06
---

# CAP theorem

Hub: [[concepts]]

The CAP theorem, in Brewer's own phrasing, "asserts that any networked
shared-data system can have only two of three desirable properties"
(consistency, availability and partition tolerance) ([[src-brewer-cap-twelve-years]]).

Brewer's later view is that "2 of 3" misleads. "CAP prohibits only a tiny part
of the design space", because partitions are rare, so a system can offer both
consistency and availability most of the time. He recommends deciding ahead of
time what the system does in a partition, in steps that begin with "detect
partitions, enter an explicit partition mode" and end with recovery
([[src-brewer-cap-twelve-years]]).

He also ties CAP to latency: "Thus, pragmatically, a partition is a time bound
on communication." A request that waits longer than that bound is, in effect,
facing a partition ([[src-brewer-cap-twelve-years]]).

[[dynamo]] chose availability and accepted weaker consistency; [[spanner]]'s
authors claim strong consistency across the globe. Both are covered in their
own notes.

## Gap

The formal proof (Gilbert and Lynch, 2002) could not be read: the publisher
returned an error and the author's copy was an unreadable scan. Nothing here
states what the theorem proves exactly, only Brewer's description of it. The
paper is the next thing to ingest.

## Related

- [[consistency-models]]
- [[when-is-strong-consistency-worth-it]]
- [[flp-impossibility]]
