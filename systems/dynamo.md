---
title: Dynamo
type: system
status: draft
tags: [replication, availability]
created: 2026-11-06
updated: 2026-11-06
---

# Dynamo

Hub: [[systems]]

Dynamo is a key-value store built for Amazon's platform and used by some of
its core services for an "always-on" experience ([[src-dynamo-paper]]).

## The choice it made

The abstract says it plainly: "To achieve this level of availability, Dynamo
sacrifices consistency under certain failure scenarios." The motivating
example is the shopping cart, which "requires that it can always write to and
read from its data store" even when disks fail, network routes flap or data
centers are lost ([[src-dynamo-paper]]). This is the availability side of the
trade-off in [[cap-theorem]].

## How it keeps going

- **Eventual consistency.** Updates "propagated to all replicas
  asynchronously" ([[consistency-models]]).
- **Versions and conflicts.** Each version of an object carries a
  [[vector-clocks|vector clock]]. If one version's clock is an ancestor of
  another's it can be forgotten; otherwise the two are in conflict and "require
  reconciliation", which is left to the application ([[src-dynamo-paper]]).
- **Tunable quorums.** Each store chooses N (replicas), R (read quorum) and W
  (write quorum). R + W > N gives a [[quorum]]-like system, and R and W are
  usually set below N for latency.

Other mechanisms the paper describes (a "sloppy quorum" and hinted handoff
for failed nodes, anti-entropy using trees, consistent hashing with virtual
nodes) are named in the paper and not summarized here.

## Contrast

[[spanner]] sits at the other end: strong consistency across the globe.

## Related

- [[quorum]]
- [[vector-clocks]]
- [[cap-theorem]]
