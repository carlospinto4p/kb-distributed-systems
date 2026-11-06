---
title: Raft
type: algorithm
status: draft
tags: [consensus, raft]
created: 2026-11-06
updated: 2026-11-06
---

# Raft

Hub: [[consensus]]

Raft is "a consensus algorithm for managing a replicated log". Its authors say
it "produces a result equivalent to (multi-)Paxos" and is as efficient, but
has a different structure that makes it "more understandable than Paxos"
([[src-raft-paper]], abstract). The understandability claim is theirs, backed
by a study of 43 students at two universities.

## Structure

Raft separates "the key elements of consensus, such as leader election, log
replication, and safety" ([[src-raft-paper]]).

- **Strong leader.** Log entries only flow from the leader to the other
  servers.
- **Leader election.** Servers use randomized timers. A follower that hears
  nothing within its election timeout becomes a candidate, and a candidate
  that receives votes from a majority of the cluster becomes the leader
  ([[quorum]]).
- **Membership changes.** A "joint consensus" approach where the majorities
  of two configurations overlap during the transition, so the cluster keeps
  working while its membership changes.

## Safety properties

The paper lists five and says they hold at all times
([[src-raft-paper]], Figure 3):

- Election Safety: at most one leader can be elected in a given term.
- Leader Append-Only: a leader never overwrites or deletes entries in its log.
- Log Matching: if two logs contain an entry with the same index and term,
  the logs are identical up to that index.
- Leader Completeness: a committed entry is present in the logs of the leaders
  of all higher-numbered terms.
- State Machine Safety: no two servers apply different entries at the same
  index.

## Compared with Paxos

See [[paxos]]. The two solve the same [[consensus-problem]] and both are used
to build a [[replicated-state-machine]]. Which is easier to learn is the Raft
authors' claim; no independent comparison was read.

## Related

- [[paxos]]
- [[consensus-problem]]
- [[flp-impossibility]]
