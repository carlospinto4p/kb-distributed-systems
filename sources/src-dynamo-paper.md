---
title: "Dynamo: Amazon's Highly Available Key-value Store"
type: source
status: draft
tags: [replication, availability]
created: 2026-11-06
updated: 2026-11-07
url: https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf
publisher: ACM, Proceedings of the 21st ACM Symposium on Operating Systems Principles (SOSP '07), Stevenson, Washington, October 14-17, 2007
author: Giuseppe DeCandia, Deniz Hastorun, Madan Jampani, Gunavardhan Kakulapati, Avinash Lakshman, Alex Pilchin, Swaminathan Sivasubramanian, Peter Vosshall, Werner Vogels
published: 2007
read: 2026-11-06
---

# Dynamo: Amazon's Highly Available Key-value Store

## Summary

The paper describes Dynamo, a key-value store that some of Amazon's core
services use to stay always writable. It gives up consistency under some
failure scenarios to do so. It uses object versioning with vector clocks and
leaves conflict resolution to the application, and it uses configurable
quorum values to trade latency against consistency.

## Key passages

- "To achieve this level of availability, Dynamo sacrifices consistency under
  certain failure scenarios." (Abstract)
- "It makes extensive use of object versioning and application-assisted
  conflict resolution" (Abstract)
- "Dynamo uses vector clocks in order to capture causality between different
  versions of the same object." (4 System Architecture)
- "A vector clock is effectively a list of (node, counter) pairs." (same)
- "Dynamo provides eventual consistency, which allows for updates to be
  propagated to all replicas asynchronously." (same)
- "R is the minimum number of nodes that must participate in a successful
  read operation. W is the minimum number of nodes that must participate in a
  successful write operation. Setting R and W such that R + W > N yields a
  quorum-like system." (same)
- "R and W are usually configured to be less than N, to provide better
  latency." (same)
- The shopping cart service "requires that it can always write to and read
  from its data store" (1 Introduction)

## Used in

- [[dynamo]]
- [[quorum]]
- [[vector-clocks]]
- [[consistency-models]]
- [[when-is-strong-consistency-worth-it]]

## Reliability

Written by Amazon's engineers about their own production system, so it is
strong on design and weak on independent measurement. The PDF carries no
venue or date in the extracted text. Venue and dates come from Werner Vogels's
post announcing the paper, which gives the reference and the ACM copyright
line "SOSP'07, October 14–17, 2007, Stevenson, Washington, USA"
([All Things Distributed](https://www.allthingsdistributed.com/2007/10/amazons_dynamo.html),
checked 2026-11-07). The ACM and dblp pages refused automated access, so the
page range and DOI are not recorded.
