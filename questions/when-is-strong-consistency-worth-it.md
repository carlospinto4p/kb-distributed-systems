---
title: When is strong consistency worth its cost?
type: question
status: draft
tags: [consistency, availability]
created: 2026-11-06
updated: 2026-11-06
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
for data that needed a stronger one. The Spanner paper's body and a
practitioner source with measurements are the places to look.

## What the notes say so far

- Weaker guarantees can be a deliberate fit: Dynamo's shopping cart must
  always accept writes ([[src-dynamo-paper]]).
- The trade is smaller than "pick two of three": Brewer says partitions are
  rare, and recommends deciding in advance how to behave during one
  ([[cap-theorem]]).
- Under a partition, a system that needs ACID isolation "can operate on at
  most one side" ([[src-brewer-cap-twelve-years]]).

## Answer

_Not answered yet._ The notes hold the two ends of the choice and no
measurements of what each costs.
