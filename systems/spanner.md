---
title: Spanner
type: system
status: draft
tags: [transactions, consistency]
created: 2026-11-06
updated: 2026-11-06
---

# Spanner

Hub: [[systems]]

Spanner is, in its authors' words, "Google's scalable, multi-version,
globally-distributed, and synchronously-replicated database"
([[src-spanner-abstract]]).

## What the abstract claims

- It is "the first system to distribute data at global scale and support
  externally-consistent distributed transactions" (the authors' claim, not
  checked).
- A "novel time API that exposes clock uncertainty" is "critical to supporting
  external consistency and a variety of powerful features"
  ([[src-spanner-abstract]]).

This is the strong-consistency end of the choice [[dynamo]] made the other way.
See [[consistency-models]] for where external consistency is mentioned.

## Gap

Only the abstract was read. How the time API works, what the transactions
guarantee exactly, and what latency the synchronous replication costs are all
unknown to this knowledge base until the full paper is ingested. That cost is
what [[when-is-strong-consistency-worth-it]] needs.

## Related

- [[dynamo]]
- [[consistency-models]]
- [[cap-theorem]]
