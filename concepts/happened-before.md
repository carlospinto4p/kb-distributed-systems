---
title: Happened-before
type: concept
status: draft
tags: [time, ordering]
created: 2026-11-06
updated: 2026-11-06
---

# Happened-before

Hub: [[concepts]]

"Happened before" is Lamport's relation for saying that one event could have
influenced another. In a distributed system it is not always possible to say
which of two events occurred first, so the relation orders only some pairs of
events. Lamport states this directly: "In a distributed system, it is
sometimes impossible to say that one of two events occurred first" and the
relation is "only a partial ordering of the events in the system"
([[src-lamport-time-clocks]]).

Two events that the relation does not order are called concurrent. Neither
could have caused the other, so any system built on top has to decide what to
do with them. [[logical-clocks]] number events consistently with the relation,
and [[vector-clocks]] go further and can tell that two events are concurrent.

## Related

- [[logical-clocks]]
- [[vector-clocks]]
- [[consensus-problem]]
