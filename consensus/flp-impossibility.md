---
title: FLP impossibility
type: concept
status: draft
tags: [consensus, impossibility]
created: 2026-11-06
updated: 2026-11-06
---

# FLP impossibility

Hub: [[consensus]]

Fischer, Lynch and Paterson show that in an asynchronous system, "every
protocol for this problem has the possibility of nontermination, even with
only one faulty process" ([[src-flp-impossibility-paper]]). The problem is
the [[consensus-problem]] for a binary value.

The paper contrasts this with the synchronous case, where "solutions are
known" ([[src-flp-impossibility-paper]]). It was first presented in March 1983
and published in the Journal of the ACM in April 1985.

What the result does not say: it does not say consensus can never be reached,
only that no protocol can guarantee it will finish. How practical algorithms
live with this (for example [[raft]] with its randomized election timers) is a
design choice described in their own papers; whether and how each one escapes
the result is not argued in the sources read here.

Hypothesis: the same shape of trade-off, where a guarantee has to be given up
under failures, is what [[cap-theorem]] describes for storage systems. Neither
source makes this link, so treat it as the author's reading.

## Gap

Only the abstract and framing were read. The proof itself was not checked.

## Related

- [[consensus-problem]]
- [[paxos]]
- [[raft]]
