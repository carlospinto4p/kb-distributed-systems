---
title: Paxos
type: algorithm
status: draft
tags: [consensus, paxos]
created: 2026-11-06
updated: 2026-11-06
---

# Paxos

Hub: [[consensus]]

Paxos solves the [[consensus-problem]] under the failure model of stopping
and restarting agents and lost or duplicated messages. Lamport's "Paxos Made
Simple" derives it from the safety requirements and calls it "among the
simplest and most obvious of distributed algorithms" ([[src-paxos-made-simple]]).

## Roles

Three kinds of agent: proposers, acceptors and learners. One process may play
more than one role ([[src-paxos-made-simple]], 2.1).

## How a value is chosen

The key move is that any two majorities of acceptors overlap, so a chosen
value cannot be missed by a later proposer ([[src-paxos-made-simple]], 2.2;
see [[quorum]]). In two steps:

1. A proposer sends a **prepare request** numbered n to a set of acceptors.
   Each acceptor replies with a promise never again to accept a proposal
   numbered less than n, and with the highest-numbered proposal it has already
   accepted, if any.
2. If the proposer hears from a majority, it sends an **accept request**
   with number n and a value: the value of the highest-numbered proposal in
   the replies, or any value it likes if none was reported.

The remaining rules (when an acceptor ignores a request, how learners find
out, how progress is achieved) are in sections 2.3 to 2.5 of the paper and are
not summarized here.

## Used for

Applying consensus once per slot of a command log gives a fault-tolerant
[[replicated-state-machine]] ([[src-paxos-made-simple]], section 3).
Lamport's earlier paper on ordering events ([[src-lamport-time-clocks]]) is
the one he points to for the state machine approach.

[[raft]] is a later algorithm that claims "a result equivalent to
(multi-)Paxos" with a different structure ([[src-raft-paper]]).

## Related

- [[consensus-problem]]
- [[raft]]
- [[quorum]]
- [[replicated-state-machine]]
