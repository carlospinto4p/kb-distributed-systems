---
title: Vector clocks
type: concept
status: draft
tags: [time, causality, replication]
created: 2026-11-06
updated: 2026-11-06
---

# Vector clocks

Hub: [[concepts]]

A vector clock records causality between versions of the same object.
Dynamo describes it as "effectively a list of (node, counter) pairs", and uses
it "in order to capture causality between different versions of the same
object" ([[src-dynamo-paper]]).

Where a [[logical-clocks|logical clock]] is one number, a vector clock keeps a
counter per node. Comparing two vector clocks can show that one version
descends from the other, in which case the older can be dropped, or that
neither does, in which case the versions are concurrent and must be reconciled
([[happened-before]]). In [[dynamo]] the reconciliation is left to the
application.

Dynamo's paper also notes that the clock can grow as more nodes handle an
object, and describes a way to limit its size ([[src-dynamo-paper]]). The
mechanism is in the paper; this note does not cover it.

## Related

- [[logical-clocks]]
- [[happened-before]]
- [[dynamo]]
