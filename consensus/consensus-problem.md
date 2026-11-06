---
title: The consensus problem
type: concept
status: draft
tags: [consensus]
created: 2026-11-06
updated: 2026-11-06
---

# The consensus problem

Hub: [[consensus]]

Several processes can each propose a value, and the system must pick one.
[[src-paxos-made-simple]] states three safety requirements:

- only a value that has been proposed may be chosen;
- only a single value is chosen;
- a process never learns that a value has been chosen unless it actually has
  been.

It sets no precise liveness requirement, only the goal that some proposed
value is eventually chosen and that a process can eventually learn it.

The same source fixes the failure model it assumes: agents "operate at
arbitrary speed, may fail by stopping, and may restart", and messages "can take
arbitrarily long to be delivered, can be duplicated, and can be lost, but they
are not corrupted" ([[src-paxos-made-simple]], 2.1). Because every agent may
fail after a value is chosen and then restart, "a solution is impossible
unless some information can be remembered by an agent that has failed and
restarted."

[[src-flp-impossibility-paper]] studies a simpler version: reliable processes
must agree on a binary value, in an asynchronous system where some may be
unreliable. [[flp-impossibility]] gives its result.

## Related

- [[flp-impossibility]]
- [[paxos]]
- [[raft]]
- [[quorum]]
