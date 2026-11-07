---
title: Spanner
type: system
status: draft
tags: [transactions, consistency]
created: 2026-11-06
updated: 2026-11-07
---

# Spanner

Hub: [[systems]]

Spanner is, in its authors' words, "Google's scalable, multi-version,
globally-distributed, and synchronously-replicated database"
([[src-spanner-paper]]).

## What it guarantees

Its transactions are externally consistent, which the paper treats as
equivalent to linearizability: if one transaction commits before another
starts, the first gets the smaller commit timestamp ([[src-spanner-paper]]).
The authors claim it was the first system to do this at global scale (their
claim, not checked). See [[consistency-models]].

## How: TrueTime and commit wait

- **TrueTime** is a clock API that returns an interval, not a single time.
  `TT.now()` returns `[earliest, latest]`, guaranteed to contain the real
  time at the call ([[src-spanner-paper]]).
- The width of that interval comes from GPS and atomic-clock time masters in
  every datacenter. In production the error bound moved between about 1 and
  7 ms, and was 4 ms on average most of the time ([[src-spanner-paper]]).
- **Commit wait**: a transaction's writes stay invisible until its commit
  timestamp has definitely passed (`TT.after(s)` is true). That wait is what
  makes timestamps match the real order of commits, and it is why Spanner
  "slows down to wait out that uncertainty" when clocks are less certain
  ([[src-spanner-paper]]).

## Transactions and reads

- **Read-write transactions** use two-phase locking, and two-phase commit
  across Paxos groups when they touch more than one ([[src-spanner-paper]]).
  The authors chose this knowingly: they would rather programmers deal with
  slow transactions than code "around the lack of transactions".
- **Read-only transactions** must be declared as such in advance. They run
  at a timestamp the system picks, take no locks, and do not block writes.
- **Snapshot reads** are reads in the past, also lock-free, at a timestamp
  the client gives or a staleness bound it allows.

## What it costs

- In microbenchmarks with replicas less than 1 ms apart, a write took about
  14 ms whether there were 1, 3 or 5 replicas. Commit wait was about 5 ms of
  that and Paxos about 9 ms. Lock-free reads took 1.2 to 1.4 ms
  ([[src-spanner-paper]], Table 3).
- In production, as measured by F1 over 24 hours: reads averaged 8.7 ms,
  single-site commits 72.3 ms and multi-site commits 103.0 ms
  ([[src-spanner-paper]], Table 6).

This is the strong-consistency end of the choice [[dynamo]] made the other
way. Whether that cost is worth paying is the open question in
[[when-is-strong-consistency-worth-it]].

## Related

- [[dynamo]]
- [[consistency-models]]
- [[cap-theorem]]
