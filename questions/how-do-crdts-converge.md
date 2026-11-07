---
title: How do conflict-free replicated data types converge?
type: question
status: draft
tags: [replication, crdt]
created: 2026-11-06
updated: 2026-11-07
---

# How do conflict-free replicated data types converge?

Hub: [[questions]]

## Why it matters

[[dynamo]] leaves conflicting versions to the application to reconcile. A data
type that merges by itself would remove that burden. Whether and when that
works decides how far weaker consistency can go without pushing the problem
back onto developers.

## What would answer it

The original paper on conflict-free replicated data types (Shapiro, Preguiça,
Baquero and Zawirski, 2011) and a precise statement of the guarantee. Read
2026-11-07 from the authors' research report: [[src-crdt-paper]].

## What the notes say so far

Brewer's article is reported to credit these types with automatic convergence
after a partition (unverified: that part of the article was only available as
a summary, see [[src-brewer-cap-twelve-years]]).

## Answer

**The guarantee.** Replicas that have received the same set of updates are in
the same state, whatever order the updates arrived in. The paper calls this
strong convergence, and with eventual delivery and termination, Strong
Eventual Consistency ([[src-crdt-paper]]). Every replica accepts reads and
writes during a partition, and no consensus is needed ([[src-crdt-paper]]).

**Two ways to get it** ([[src-crdt-paper]]):

- **State-based.** Replicas send each other their whole state. The states
  form a join semilattice, merge takes the least upper bound, and every
  update only moves the state up. Merge is then commutative, idempotent and
  associative, so it does not matter how often or in which order states are
  merged.
- **Operation-based.** Replicas send each other the update operations,
  delivered in causal order (see [[happened-before]]). Operations that are
  concurrent must commute, so applying them in either order gives the same
  state.

The paper proves each style can emulate the other.

**Examples** ([[src-crdt-paper]]): a vector of counters merged by taking the
maximum at each index (which is a [[vector-clocks|vector clock]] when each
process only increments its own entry); a counter that goes up and down,
built from two increment-only counters; a set that only grows; and a set
with removals, built from an add set and a remove set.

**What it does not do.** Convergence says the replicas agree, not that the
result is what a single machine would have produced. When the same element
is added and removed concurrently, the designer chooses whether the add or
the remove wins, and either choice converges. The paper shows such a set can
reach states no sequential execution allows, so this guarantee is not
comparable with sequential consistency ([[src-crdt-paper]]).

My reading: this is the same decision Dynamo leaves to the application. A
CRDT does not remove it; it makes it once, in the data type, instead of in
every application.
