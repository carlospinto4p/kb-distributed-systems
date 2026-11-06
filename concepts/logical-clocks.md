---
title: Logical clocks
type: concept
status: draft
tags: [time, ordering]
created: 2026-11-06
updated: 2026-11-06
---

# Logical clocks

Hub: [[concepts]]

A logical clock gives every event a number so that the numbers respect
[[happened-before]]. Lamport's requirement, the Clock Condition, is: for any
events a and b, if a happened before b then the clock value of a is smaller
than that of b ([[src-lamport-time-clocks]]).

The converse is deliberately not required. The paper says "we cannot expect
the converse condition to hold as well", because that would force every pair
of concurrent events to carry the same time. So a smaller number does not
prove one event came first; it only means the other cannot have come first.

Two implementation rules are enough ([[src-lamport-time-clocks]]):

1. Each process increments its clock between any two successive events.
2. A message carries the sender's clock value, and the receiver sets its own
   clock to be greater than or equal to its present value and greater than
   the message's value.

The paper goes on to extend this partial order to a total order of all events
and uses that to solve synchronization problems ([[src-lamport-time-clocks]],
abstract). How the tie-breaking works is in the paper; this note does not
restate it.

## Related

- [[happened-before]]
- [[vector-clocks]]
