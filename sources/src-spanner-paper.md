---
title: "Spanner: Google's Globally-Distributed Database"
type: source
status: draft
tags: [transactions, consistency]
created: 2026-11-06
updated: 2026-11-07
url: https://www.usenix.org/system/files/conference/osdi12/osdi12-final-16.pdf
publisher: USENIX, 10th USENIX Symposium on Operating Systems Design and Implementation (OSDI '12)
author: James C. Corbett, Jeffrey Dean, Michael Epstein, and 23 co-authors
published: 2012
read: 2026-11-07
---

# Spanner: Google's Globally-Distributed Database

## Summary

The paper describes Spanner, Google's database that replicates data
synchronously across datacenters and gives every transaction a commit
timestamp that reflects the real order of commits. That property, external
consistency, rests on TrueTime: a clock API that returns an interval
guaranteed to contain the real time, instead of a single value. When the
interval is wide, Spanner waits it out before making a commit visible
("commit wait"). Read-write transactions take locks and use two-phase commit
over Paxos groups; read-only transactions and reads in the past take no
locks. The paper reports latencies from microbenchmarks and from F1, Google's
advertising backend.

The venue is printed in each page footer of the PDF. The abstract was first
read on the publication page,
https://research.google/pubs/spanner-googles-globally-distributed-database-2/,
on 2026-11-06.

## Key passages

- "Spanner is Google's scalable, multi-version, globally-distributed, and
  synchronously-replicated database." (Abstract)
- External consistency, "or equivalently, linearizability": "if a transaction
  T1 commits before another transaction T2 starts, then T1's commit timestamp
  is smaller than T2's." (1 Introduction)
- "If the uncertainty is large, Spanner slows down to wait out that
  uncertainty." The implementation "keeps uncertainty small (generally less
  than 10ms) by using multiple modern clock references (GPS and atomic
  clocks)." (1 Introduction)
- "We believe it is better to have application programmers deal with
  performance problems due to overuse of transactions as bottlenecks arise,
  rather than always coding around the lack of transactions. Running
  two-phase commit over Paxos mitigates the availability problems." (2.3 Data
  Model)
- TrueTime API, Table 1: `TT.now()` returns "TTinterval: [earliest, latest]";
  `TT.after(t)` is "true if t has definitely passed"; `TT.before(t)` is "true
  if t has definitely not arrived". (3 TrueTime)
- "The TT.now() method returns a TTinterval that is guaranteed to contain the
  absolute time during which TT.now() was invoked." (3 TrueTime)
- The error bound ε is "typically a sawtooth function of time, varying from
  about 1 to 7 ms over each poll interval." The average is "therefore 4 ms
  most of the time." (3 TrueTime; the Greek letters are lost in the PDF's
  text layer and were restored from the paper's definition of ε)
- "A read-only transaction must be predeclared as not having any writes".
  "Reads in a read-only transaction execute at a system-chosen timestamp
  without locking, so that incoming writes are not blocked." (4.1 Timestamp
  Management)
- "A snapshot read is a read in the past that executes without locking."
  (4.1 Timestamp Management)
- Commit wait: "The coordinator leader ensures that clients cannot see any
  data committed by Ti until TT.after(si) is true." (4.1.2 Assigning
  Timestamps to RW Transactions)
- "Transactional reads and writes use two-phase locking." (4.1.2 Assigning
  Timestamps to RW Transactions)
- "From the 1-replica experiments, commit wait is about 5ms, and Paxos
  latency is about 9ms." (5.1 Microbenchmarks)
- Table 3, microbenchmarks with clients and replicas less than 1 ms apart, 4KB
  operations served from memory: write latency 14.4±1.0 ms with 1 replica,
  13.9±.6 ms with 3, 14.4±.4 ms with 5, and 9.4±.6 ms with 1 replica and
  commit wait disabled; read-only transactions 1.3 to 1.4 ms; snapshot reads
  1.2 to 1.3 ms. (5.1 Microbenchmarks)
- Table 6, latencies seen by F1 over 24 hours: all reads mean 8.7 ms (std dev
  376.4, 21.5B operations); single-site commit mean 72.3 ms (std dev 112.8,
  31.2M); multi-site commit mean 103.0 ms (std dev 52.2, 32.1M). "The large
  standard deviation in write latencies is caused by a pretty fat tail due to
  lock conflicts." (5.4 F1)

## Used in

- [[spanner]]
- [[consistency-models]]
- [[when-is-strong-consistency-worth-it]]

## Reliability

Written by Google's engineers about their own production system. The
measurements are theirs and were not reproduced. "First system" claims in the
abstract and introduction are the authors' own. Quotes were taken from a text
extraction of the PDF and checked against the paper's section headings.
