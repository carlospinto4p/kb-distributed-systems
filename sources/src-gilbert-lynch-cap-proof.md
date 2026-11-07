---
title: "Brewer's Conjecture and the Feasibility of Consistent, Available, Partition-Tolerant Web Services"
type: source
status: draft
tags: [cap, consistency, availability]
created: 2026-11-07
updated: 2026-11-07
url: https://www.comp.nus.edu.sg/~gilbert/pubs/BrewersConjecture-SigAct.pdf
publisher: ACM SIGACT News, volume 33, issue 2, pages 51-59, DOI 10.1145/564585.564601
author: Seth Gilbert, Nancy Lynch
published: 2002-06
read: 2026-11-07
---

# Brewer's Conjecture and the Feasibility of Consistent, Available, Partition-Tolerant Web Services

## Summary

The paper turns Brewer's CAP conjecture into a theorem. It defines
consistency as atomic (linearizable) data, availability as every request to
a non-failing node getting a response, and partition tolerance as a network
that may lose any number of messages. It proves that no read/write object
can be both available and atomic when messages may be lost, first in an
asynchronous network and then in a partially synchronous one, where nodes
have clocks. It then shows that with clocks a system can be atomic whenever
no messages are lost, and defines a weaker guarantee, Delayed-t consistency,
that bounds how long stale reads last after a partition heals.

## Key passages

- "It is impossible in the asynchronous network model to implement a
  read/write data object that guarantees the following properties:
  Availability, Atomic consistency in all fair executions (including those
  in which messages are lost)." (Theorem 1, 3.1)
- Atomic consistency: "there must exist a total order on all operations
  such that each operation looks as if it were completed at a single
  instant." (2.1)
- "any read operation that begins after a write operation completes must
  return that value, or the result of a later write operation." (2.1)
- Availability: "every request received by a non-failing node in the system
  must result in a response." (2.2) The paper notes this puts "no bound on
  how long the algorithm may run before terminating". (same)
- Partition tolerance: "the network will be allowed to lose arbitrarily many
  messages sent from one node to another." (2.3)
- The proof splits the nodes into two groups and loses every message between
  them: "if a write occurs in G1, and later a read occurs in G2, then the
  read operation cannot return the results of the earlier write operation."
  (3.1)
- "any two of these three properties can be achieved." (3.2)
- In the asynchronous model, an algorithm "has no way of determining whether
  a message has been lost, or has been arbitrarily delayed" (Corollary 1.1),
  so it cannot even be atomic in the executions where no message is lost.
- With clocks, "There are partially synchronous algorithms that will return
  atomic data when all messages in an execution are delivered (i.e., there
  are no partitions), and will only return inconsistent (and, in particular,
  stale) data when messages are lost." (4.3)
- Real systems "are forced to settle with returning 'most of the data, most
  of the time.'" (5 Conclusion)

## Used in

- [[cap-theorem]]
- [[consistency-models]]

## Reliability

Peer-reviewed formal proof by the authors who stated the theorem; this is
the primary source for what CAP proves. The copy read is the PDF on Seth
Gilbert's university page, read in full as extracted text. The PDF names no
venue or date; those come from Crossref's record for the title
([Crossref](https://api.crossref.org/works?query.bibliographic=Brewer%27s+conjecture+and+the+feasibility+of+consistent+available+partition-tolerant+web+services&rows=1),
checked 2026-11-07). A copy hosted at CMU is a scan whose text cannot be
extracted, which is why the first attempt failed.
