---
title: How do conflict-free replicated data types converge?
type: question
status: draft
tags: [replication, crdt]
created: 2026-11-06
updated: 2026-11-06
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
Baquero and Zawirski, 2011) and a precise statement of the guarantee. The
HAL page for that paper blocked the fetch with a bot-protection page, so it
could not be read. Another copy of the paper is needed.

## What the notes say so far

Brewer's article is reported to credit these types with automatic convergence
after a partition (unverified: that part of the article was only available as
a summary, see [[src-brewer-cap-twelve-years]]). Nothing else is known here.

## Answer

_Not answered yet._
