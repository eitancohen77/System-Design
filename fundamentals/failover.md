---
layout: default
title: CAP Theorem
---

[← Back to all topics](../index.md)

# CAP Theorem — Consistency vs. Availability

**Code:** [Failover Demonstration](https://github.com/eitancohen77/Availability-Failover)

A dependency-free simulation demonstrating the CAP trade-off using two independent
5-node clusters — one tuned for consistency (CP), one tuned for availability (AP).

## The idea

_(Paste your polished notes here — the ATM/partition explanation, quorum, hinted
handoff, sloppy quorum, etc. This is the same content as your repo README, just
reachable from the hub too.)_

## Watching it run

Since this is a live multi-node simulation, here's what an actual run looks like
rather than a live demo:

```
$ python3 main.py
[Normal operation] CP cluster: balance=100 across all 5 nodes
[Normal operation] AP cluster: balance=100 across all 5 nodes

[Partition introduced] nodes {0,1} cut off from {2,3,4}

[Write balance=250 to node 0, both systems]
  CP → REJECTED (only 2/5 nodes reachable, quorum=3)
  AP → ACCEPTED (node 0 updated, replicated to node 1 only)

[Read from majority node 2]
  CP → 100 (quorum-confirmed)
  AP → 100 (node 2's local value — node 0 is silently at 250)

[Partition healed]

[Final state]
  CP cluster: all nodes read 100 (nothing to reconcile)
  AP cluster: nodes 0,1 read 250 — nodes 2,3,4 read 100 (diverged, unresolved)
```

## What this demonstrates

- Quorum-gating and unconditional availability are mutually exclusive by definition
- An AP system needs an explicit reconciliation strategy (last-write-wins, vector
  clocks, CRDTs, read-repair) to converge after a partition heals — healing the
  network alone doesn't fix it
