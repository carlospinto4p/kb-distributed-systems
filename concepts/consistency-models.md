---
title: Consistency models
type: concept
status: draft
tags: [consistency]
created: 2026-11-06
updated: 2026-11-06
---

# Consistency models

Hub: [[concepts]]

A consistency model says what a system may and may not do when clients read
and write the same data. Jepsen defines it as "a set of histories" and as "a
safety property which declares what a system can do" ([[src-jepsen-consistency-models]]).

## What the sources support

- **A chain of strength.** For single-object models, "strict serializable
  implies linearizable, which implies sequential, which implies causal"
  ([[src-jepsen-consistency-models]]). Stronger models allow fewer histories.
- **Serializable** means "every legal history must be equivalent to a totally
  ordered execution" ([[src-jepsen-consistency-models]]).
- **Strong models cost availability.** Jepsen says models at or stronger than
  cursor stability, snapshot isolation and sequential "cannot be totally
  available in asynchronous networks" ([[src-jepsen-consistency-models]]).
  This is the same trade-off as [[cap-theorem]].
- **Eventual consistency** is what [[dynamo]] provides: updates "propagated to
  all replicas asynchronously" ([[src-dynamo-paper]]), with conflicts left to
  the application.
- **External consistency** is what [[spanner]]'s authors claim for its
  distributed transactions ([[src-spanner-abstract]]). Their abstract does not
  define it, so this note does not either.

## Gap

The Jepsen pages do not define linearizable, sequential, causal or eventual
consistency on their own, only their order. Definitions of those four are
still needed from a primary source.

## Related

- [[cap-theorem]]
- [[when-is-strong-consistency-worth-it]]
- [[quorum]]
