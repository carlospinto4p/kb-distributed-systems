---
title: Replicated state machine
type: concept
status: draft
tags: [replication, consensus]
created: 2026-11-06
updated: 2026-11-06
---

# Replicated state machine

Hub: [[concepts]]

A replicated state machine keeps several servers in the same state by having
them all apply the same commands in the same order. Consensus is what makes
the order agree: each slot in the sequence of commands is one consensus
decision.

Both [[paxos]] and [[raft]] are described this way. Lamport says the complete
Paxos algorithm "is obtained by the straightforward application of consensus
to the state machine approach for building a distributed system"
([[src-paxos-made-simple]]). Raft's abstract opens with "Raft is a consensus
algorithm for managing a replicated log" ([[src-raft-paper]]); the log is the
ordered list of commands.

## Related

- [[consensus-problem]]
- [[paxos]]
- [[raft]]
