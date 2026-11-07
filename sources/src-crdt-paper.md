---
title: "Conflict-free Replicated Data Types"
type: source
status: draft
tags: [replication, crdt, consistency]
created: 2026-11-07
updated: 2026-11-07
url: https://www.lip6.fr/Marc.Shapiro/papers/RR-7687.pdf
publisher: INRIA research report RR-7687, version 2; also in Stabilization, Safety, and Security of Distributed Systems (SSS 2011), Lecture Notes in Computer Science, pages 386-400, DOI 10.1007/978-3-642-24550-3_29
author: Marc Shapiro, Nuno Preguiça, Carlos Baquero, Marek Zawirski
published: 2011-08-25
read: 2026-11-07
---

# Conflict-free Replicated Data Types

## Summary

The paper defines Strong Eventual Consistency (SEC): replicas that have
received the same updates are in the same state. It is meant to avoid the
rollbacks and the consensus that other eventually consistent systems use to
settle conflicts. It gives two sufficient conditions for it. In the state-based
style, replica states form a join semilattice, merge takes the least upper
bound, and updates only move the state up. In the operation-based style,
updates are delivered in causal order and concurrent updates commute. Data
types that meet either condition are CRDTs; the paper proves the two styles
can emulate each other, and gives counters, sets, a log and a directed graph
as examples.

## Key passages

- Eventual consistency (Definition 2.2): eventual delivery, convergence
  ("Correct replicas that have delivered the same updates eventually reach
  equivalent state"), and termination. (2.2)
- Strong convergence (Definition 2.3): "Correct replicas that have delivered
  the same updates have equivalent state". (2.2)
- The merge operator is "commutative", "idempotent" and "associative". (2.3)
- Theorem 2.1: "any state-based object that satisfies the monotonic
  semilattice property is SEC", assuming eventual delivery and termination.
  (2.3)
- "a sufficient condition for convergence of an op-based object is that all
  its concurrent operations commute." (2.4) Theorem 2.2 adds that updates
  must be delivered in causal order. (same)
- "A SEC replica is always available for both reads and writes,
  independently of network conditions." (3.1)
- "SEC does not require to solve consensus." (3.1)
- A counter that goes up and down is built from "two increment-only counters
  I and D", with value |I| - |D|. (4.1)
- For a set where the same element is added and removed concurrently, "the
  add could win, or the remove could win" and all such choices "satisfy the
  strong convergence condition". (3.3)
- "SEC is incomparable with sequential consistency." (3.3)
- Key-value stores "such as Dynamo [3] and Riak" use the state-based
  approach. (6)

## Used in

- [[how-do-crdts-converge]]
- [[consistency-models]]

## Reliability

Written by the researchers who introduced the term; the primary source for
the definitions. The copy read is the INRIA research report, version 2 of
25 August 2011, from Marc Shapiro's page at LIP6, read in full as extracted
text except section 5, on the directed graph, which was not read. The conference
version in SSS 2011 was not read and may differ; its venue and pages come
from Crossref
([Crossref](https://api.crossref.org/works?query.bibliographic=Conflict-free+replicated+data+types+Shapiro+Preguica+Baquero+Zawirski&rows=1),
checked 2026-11-07). The HAL copy of the report is behind a bot check.
