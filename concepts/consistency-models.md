---
title: Consistency models
type: concept
status: draft
tags: [consistency]
created: 2026-11-06
updated: 2026-11-07
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
- **Linearizable** (Gilbert and Lynch call it atomic): "there must exist a
  total order on all operations such that each operation looks as if it were
  completed at a single instant" ([[src-gilbert-lynch-cap-proof]]).
- **Eventual consistency** is what [[dynamo]] provides: updates "propagated to
  all replicas asynchronously" ([[src-dynamo-paper]]), with conflicts left to
  the application. Shapiro and others define it as eventual delivery, plus
  "Correct replicas that have delivered the same updates eventually reach
  equivalent state", plus termination ([[src-crdt-paper]]).
- **Strong eventual consistency** drops the "eventually": replicas that have
  delivered the same updates are in the same state at once. It is what
  conflict-free replicated data types provide; see [[how-do-crdts-converge]]
  ([[src-crdt-paper]]).
- **External consistency** is what [[spanner]] provides for its distributed
  transactions. Its paper calls it equivalent to linearizability and defines
  it by commit order: "if a transaction T1 commits before another transaction
  T2 starts, then T1's commit timestamp is smaller than T2's"
  ([[src-spanner-paper]]).

## Gap

The Jepsen pages do not define linearizable, sequential, causal or eventual
consistency on their own, only their order. Linearizable and eventual now
have primary definitions above; sequential and causal still need one.

## Related

- [[cap-theorem]]
- [[how-do-crdts-converge]]
- [[when-is-strong-consistency-worth-it]]
- [[quorum]]
