---
title: Time, Clocks, and the Ordering of Events in a Distributed System
type: source
status: draft
tags: [time, ordering]
created: 2026-11-06
updated: 2026-11-06
url: https://lamport.azurewebsites.net/pubs/time-clocks.pdf
publisher: Communications of the ACM
author: Leslie Lamport
published: 1978-07
read: 2026-11-06
---

# Time, Clocks, and the Ordering of Events in a Distributed System

## Summary

Lamport defines a "happened before" relation between events in a distributed
system and shows it is only a partial order. He then gives a rule for
numbering events with logical clocks so that the numbers respect that order,
and shows how those numbers can be turned into a total order. The last part
adapts the algorithm to physical clocks and bounds how far they can drift
apart.

## Key passages

- "In a distributed system, it is sometimes impossible to say that one of two
  events occurred first." (Introduction)
- "The relation "happened before" is therefore only a partial ordering of the
  events in the system." (Introduction)
- Clock Condition: "For any events a, b: if a → b then C(a) < C(b)."
  (The Partial Ordering, as typeset in the PDF)
- "we cannot expect the converse condition to hold as well" (same section)
- IR1: "Each process Pi increments Ci between any two successive events."
- IR2(b): "Upon receiving a message m, process Pi sets Ci greater than or
  equal to its present value and greater than Tm."

## Used in

- [[happened-before]]
- [[logical-clocks]]
- [[paxos]]

## Reliability

The primary paper. The PDF on the author's site is a scan with a text layer,
so some characters in the extracted text are garbled (the arrow is rendered
as dashes); the quotes above restore only those symbols. The publication
month is read from the running page header ("Communications of the ACM, July
1978, Volume 21").
