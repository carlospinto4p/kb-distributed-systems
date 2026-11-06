---
title: Concepts
type: hub
status: draft
tags: []
created: 2026-11-06
updated: 2026-11-06
---

# Concepts

Back to [[index]].

The ideas the algorithms and systems are built from.

## Time and ordering

- [[happened-before]]: the partial order on events that needs no clock.
- [[logical-clocks]]: numbers that respect that order.
- [[vector-clocks]]: lists of counters that can also detect concurrent updates.

## Agreement and copies of data

- [[quorum]]: how many replicas must answer for a read or write to count.
- [[replicated-state-machine]]: copies that stay equal by applying the same commands in the same order.
- [[consistency-models]]: what a system promises about what readers see.
- [[cap-theorem]]: the trade-off while the network is partitioned.
