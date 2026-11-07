---
title: When is strong consistency worth its cost?
type: question
status: draft
tags: [consistency, availability]
created: 2026-11-06
updated: 2026-11-07
---

# When is strong consistency worth its cost?

Hub: [[questions]]

## Why it matters

Choosing a storage system means choosing a point between [[dynamo]]
(always writable, weaker guarantees) and [[spanner]] (strong guarantees,
synchronous replication). The choice should follow what the data is used for.

## What would answer it

Measured latency and availability for both kinds of system under the same
workload, and a worked example of what goes wrong when a weaker model is used
for data that needed a stronger one. Spanner's side is now measured (below);
Dynamo's latencies and a practitioner source with a failure example are the
places to look next.

## What the notes say so far

- Weaker guarantees can be a deliberate fit: Dynamo's shopping cart must
  always accept writes ([[src-dynamo-paper]]).
- The trade is smaller than "pick two of three": Brewer says partitions are
  rare, and recommends deciding in advance how to behave during one
  ([[cap-theorem]]).
- Under a partition, a system that needs ACID isolation "can operate on at
  most one side" ([[src-brewer-cap-twelve-years]]).
- Spanner's price, in its own production numbers: single-site commits
  averaged 72.3 ms and multi-site commits 103.0 ms, while reads averaged
  8.7 ms. About 5 ms of each write is commit wait ([[src-spanner-paper]]).
- Spanner's authors chose to pay it: programmers should deal with slow
  transactions "as bottlenecks arise, rather than always coding around the
  lack of transactions" ([[src-spanner-paper]]).

## Answer

_Not answered yet._ The notes now hold Spanner's measured cost but nothing
comparable for Dynamo, so the two ends cannot be compared yet.
