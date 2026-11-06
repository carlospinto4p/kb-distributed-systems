---
title: Paxos Made Simple
type: source
status: draft
tags: [consensus, paxos]
created: 2026-11-06
updated: 2026-11-06
url: https://lamport.azurewebsites.net/pubs/paxos-simple.pdf
publisher: Author's website (dated 01 Nov 2001 on the first page)
author: Leslie Lamport
published: 2001-11-01
read: 2026-11-06
---

# Paxos Made Simple

## Summary

A short, plain-language derivation of the Paxos consensus algorithm from the
properties it must satisfy. It names three roles (proposers, acceptors,
learners), shows how a value is chosen with a prepare phase and an accept
phase, and then applies consensus to the state machine approach to build a
fault-tolerant system.

## Key passages

- "The Paxos algorithm, when presented in plain English, is very simple."
  (Abstract)
- Safety: "Only a value that has been proposed may be chosen, Only a single
  value is chosen, and A process never learns that a value has been chosen
  unless it actually has been." (2.1 The Problem)
- Model: "Agents operate at arbitrary speed, may fail by stopping, and may
  restart." (2.1)
- Model: "Messages can take arbitrarily long to be delivered, can be
  duplicated, and can be lost, but they are not corrupted." (2.1)
- A prepare request asks an acceptor for "A promise never again to accept a
  proposal numbered less than n" and for the highest-numbered proposal it
  has already accepted. (2.2 Choosing a Value)
- "The last section explains the complete Paxos algorithm, which is obtained
  by the straightforward application of consensus to the state machine
  approach for building a distributed system" (1 Introduction)

## Used in

- [[paxos]]
- [[consensus-problem]]
- [[replicated-state-machine]]
- [[quorum]]

## Reliability

Written by the algorithm's author. The date comes from the first page of the
PDF. It is an exposition, not the original presentation of Paxos, which the
text itself describes as "Greek to many readers"; the original was not read.
