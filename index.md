---
layout: default
title: System Design Deep Dives
---

# System Design Deep Dives

Notes and working code covering core distributed systems concepts, plus case studies
on how real systems (Kafka, Redis, etc.) apply — or break — these trade-offs.

## Fundamentals

Hands-on demos I built from scratch to prove out each concept.

- [Networking Layers](fundamentals/networking-layers.md) — OSI Model, The 3 Important Layers
- [CAP Theorem](fundamentals/cap-theorem.md) — consistency vs. availability during a network partition
- [Consistency Patterns](fundamentals/consistency-systems.md) — strong vs eventual consistency
- [Availability](fundamentals/availability.md) — availability, rule of 9s, fault tolerance
- [Failover](fundamentals/failover.md) — active-passive & active-active failover
- [Replication](fundamentals/replication.md) — single vs. master-slave, full vs. partial replication
- [DNS](fundamentals/dns.md) — Domain Name System: 4 DNS servers

## Case Studies

Analysis of decisions real systems made, and how they map back to the fundamentals above.
