---
title: CAP theorem
type: concept
status: draft
tags: [cap, consistency, availability]
created: 2026-11-06
updated: 2026-11-07
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

## What the proof shows

Gilbert and Lynch made the conjecture a theorem. Their terms are narrow
([[src-gilbert-lynch-cap-proof]]):

- **Consistency** is atomic (linearizable) data: "any read operation that
  begins after a write operation completes must return that value, or the
  result of a later write operation."
- **Availability** is "every request received by a non-failing node in the
  system must result in a response", with no bound on how long that takes.
- **Partition tolerance** means the network may "lose arbitrarily many
  messages sent from one node to another."

The proof splits the nodes into two groups and loses every message between
them. A write completes in one group; a later read in the other group must
answer, and cannot have seen the write. So no read/write object is both
available and atomic once messages can be lost. This holds in an
asynchronous network and also when nodes have clocks
([[src-gilbert-lynch-cap-proof]]).

Clocks change one thing. Without them a node cannot tell a lost message from
a slow one, so it cannot be atomic even when nothing is lost. With them, a
system can be atomic whenever every message arrives, and return stale data
only while messages are being lost ([[src-gilbert-lynch-cap-proof]]). My
reading: this fits Brewer's later point, above, that a partition is in
practice a time bound on communication.

## Related

- [[consistency-models]]
- [[when-is-strong-consistency-worth-it]]
- [[flp-impossibility]]
