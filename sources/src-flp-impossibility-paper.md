---
title: Impossibility of Distributed Consensus with One Faulty Process
type: source
status: draft
tags: [consensus, impossibility]
created: 2026-11-06
updated: 2026-11-06
url: https://groups.csail.mit.edu/tds/papers/Lynch/jacm85.pdf
publisher: Journal of the ACM
author: Michael J. Fischer, Nancy A. Lynch, Michael S. Paterson
published: 1985-04
read: 2026-11-06
---

# Impossibility of Distributed Consensus with One Faulty Process

## Summary

The paper studies consensus in an asynchronous system where some processes
may be unreliable, and the reliable ones must agree on a binary value. It
proves that no protocol can be guaranteed to finish, even if only one
process can fail. It contrasts this with the synchronous case, for which
solutions are known.

## Key passages

- "every protocol for this problem has the possibility of nontermination,
  even with only one faulty process." (Abstract)
- "The problem is for the reliable processes to agree on a binary value."
  (Abstract)
- "By way of contrast, solutions are known for the synchronous case"
  (Abstract)
- First presented at "the 2nd ACM Symposium on Principles of Database
  Systems, March 1983" (front matter)

## Used in

- [[flp-impossibility]]
- [[consensus-problem]]

## Reliability

The primary paper, journal version (Vol. 32, No. 2, April 1985, pp. 374-382).
The PDF is a scan with a text layer; the abstract's wording was read from
that layer and has a few missing spaces that the quotes above repair. Only
the abstract and the framing were read closely; the proof was not checked.
