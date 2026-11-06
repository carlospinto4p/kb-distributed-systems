---
title: Jepsen consistency models
type: source
status: draft
tags: [consistency]
created: 2026-11-06
updated: 2026-11-06
url: https://jepsen.io/consistency/models
publisher: Jepsen
author: Jepsen
published: undated
read: 2026-11-06
---

# Jepsen consistency models

## Summary

Jepsen's reference pages on consistency models. They define a consistency
model as a set of histories, and arrange single-object models in a chain
from strongest to weaker. They also say which models cannot stay available
during network partitions.

## Key passages

- "A consistency model is a safety property which declares what a system can
  do." (jepsen.io/consistency, Models)
- "A consistency model is a set of histories." (/consistency/models)
- "For single-object models, strict serializable implies linearizable, which
  implies sequential, which implies causal." (/consistency/models)
- Serializable: "every legal history must be equivalent to a totally ordered
  execution." (jepsen.io/consistency, Models)
- "All models at or stronger than cursor stability, snapshot isolation, and
  sequential cannot be totally available in asynchronous networks."
  (/consistency/models)

## Used in

- [[consistency-models]]

## Reliability

A well-known practitioner reference, not a peer-reviewed paper. The pages
show no date and name no individual author. The pages give no standalone
definitions of linearizable, sequential, causal or eventual consistency (only
their order), so those definitions are not in this knowledge base.
