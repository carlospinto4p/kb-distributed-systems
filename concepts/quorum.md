---
title: Quorum
type: concept
status: draft
tags: [replication, consensus]
created: 2026-11-06
updated: 2026-11-06
---

# Quorum

Hub: [[concepts]]

A quorum is the number of replicas that must take part in an operation for it
to count. Two systems in this knowledge base use it in different ways.

**Majorities in consensus.** [[paxos]] and [[raft]] act once a majority of
servers has responded. Raft's authors say typical consensus algorithms "make
progress when any majority of their servers is available" (project page
linked from [[src-raft-paper]]) and a Raft entry counts as committed once it
is replicated on a majority. Paxos relies on the fact that any two majorities
share at least one member ([[src-paxos-made-simple]], 2.2).

**Configurable R and W in storage.** [[dynamo]] makes the sizes tunable: R is
the minimum number of nodes that must take part in a read, W the minimum for a
write, and "Setting R and W such that R + W > N yields a quorum-like system"
where N is the number of replicas ([[src-dynamo-paper]]). The paper adds that
R and W are usually set below N for better latency, since an operation waits
for the slowest of the R or W replicas it needs.

## Related

- [[consensus-problem]]
- [[dynamo]]
- [[raft]]
