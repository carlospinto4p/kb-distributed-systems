---
title: In Search of an Understandable Consensus Algorithm (Extended Version)
type: source
status: draft
tags: [consensus, raft]
created: 2026-11-06
updated: 2026-11-06
url: https://raft.github.io/raft.pdf
publisher: Stanford University (USENIX ATC 2014 for the shorter version)
author: Diego Ongaro, John Ousterhout
published: 2014
read: 2026-11-06
---

# In Search of an Understandable Consensus Algorithm (Extended Version)

## Summary

The paper presents Raft, a consensus algorithm for managing a replicated log.
It claims the same result as multi-Paxos and the same efficiency, with a
structure meant to be easier to understand. It splits the problem into
leader election, log replication and safety, and adds a way to change the
cluster's membership. A user study with 43 students is used as evidence of
understandability.

## Key passages

- "Raft is a consensus algorithm for managing a replicated log." (Abstract)
- "It produces a result equivalent to (multi-)Paxos, and it is as efficient
  as Paxos, but its structure is different from Paxos" (Abstract)
- "Raft separates the key elements of consensus, such as leader election,
  log replication, and safety" (Abstract)
- "Leader election: Raft uses randomized timers to elect leaders."
  (1 Introduction)
- Safety properties named in the paper's Figure 3: Election Safety, Leader
  Append-Only, Log Matching, Leader Completeness, State Machine Safety.
- "Election Safety: at most one leader can be elected in a given term."
  (Figure 3)
- Project page: "A slightly shorter version of this paper received a Best
  Paper Award at the 2014 USENIX Annual Technical Conference."
  (https://raft.github.io/, Publications)

## Used in

- [[raft]]
- [[paxos]]
- [[replicated-state-machine]]
- [[quorum]]

## Reliability

Written by Raft's designers, so claims that Raft is better than Paxos are the
authors' own, backed by their study. The PDF gives no date for the extended
version; the year comes from the project page's note about the 2014 ATC
paper. The text was read from the PDF; the proofs were not checked.
