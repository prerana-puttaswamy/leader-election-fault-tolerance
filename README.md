# Leader Election Under Crash-Recovery Fault Models

> Academic Research — Distributed Systems  
> California State University, Long Beach | 2025  
> Author: Prerana Puttaswamy

---

## About

In distributed systems, **leader election** is a fundamental problem — when nodes crash, which node takes over? How quickly? How many messages does it take? And what happens when the network itself is partitioned?

This research simulates and evaluates leader election algorithms under realistic failure conditions including crash-recovery cycles, network partitions, and packet loss. It goes beyond standard algorithm comparison by introducing a **Multi-Attribute election strategy** that factors in CPU load and battery/resource scoring to elect more capable leaders — not just the node with the highest ID.

---

## Algorithms Studied

| Algorithm | Core Idea | Strength | Weakness |
|---|---|---|---|
| **Bully** | Highest-ID node wins, announces dominance | Simple, fast convergence | High message overhead, poor under partitions |
| **Ring** | Election token passed around a logical ring | Low message count in normal operation | Unreliable under network partitions |
| **Raft-style** | Term-based voting with majority quorum | Strong consistency guarantees | Higher latency per election round |
| **Multi-Attribute** | Weighted scoring using CPU load + resource level | Elects most capable node, lowest re-election latency | More complex scoring logic |

---

## Fault Models Simulated

- **Crash-Recovery** — nodes crash mid-election and recover, triggering re-election
- **Network Partitions** — subsets of nodes lose connectivity, splitting the cluster
- **Packet Loss** — messages dropped at configurable rates to simulate unreliable networks
- **Combined Faults** — simultaneous crashes + partitions to stress-test algorithm robustness

---

## System Architecture

The simulation engine was built with three core components:

**Event-Driven Simulation Engine**
- Discrete-event model for reproducible experiments
- Fault injection at configurable intervals and rates
- Supports crash, restart, and partition events

**Message Bus**
- Models realistic network conditions: latency, jitter, packet loss
- Configurable drop rates per simulation run

**Node State Machines**
- Each node implements its own election protocol state machine
- States: Follower, Candidate, Leader, Crashed, Recovering

---

## Key Results

- **Multi-Attribute algorithm** achieved the lowest re-election latency (~0.7s), outperforming Bully and Ring under crash-recovery scenarios
- **Bully algorithm** had the highest message overhead — up to 2x more messages than Ring under normal conditions
- **Ring algorithm** showed poor reliability under network partitions, failing to elect a leader in split-network scenarios
- **Raft-style** provided the strongest consistency guarantees but at the cost of higher per-election latency
- No single algorithm dominates all metrics — the right choice depends on network reliability, cluster size, and consistency requirements

---

## Performance Metrics

- Election latency — time from leader failure to new leader elected
- Message overhead — total messages exchanged per election round
- Success rate — percentage of elections completing under fault conditions
- Re-election frequency — how often leadership changes under sustained faults

---

## Research Paper

The full research paper is included in this repository:

📄 [Fault Leader Selection - research paper.pdf](./Fault%20Leader%20Selection%20-%20research%20paper.pdf)

---

## Concepts & Technologies

| Area | Topics |
|---|---|
| Distributed Systems | Leader election, consensus, fault tolerance |
| Algorithms | Bully, Ring, Raft, Multi-Attribute scoring |
| Fault Models | Crash-recovery, network partition, packet loss |
| System Design | Event-driven simulation, state machines, message bus |
| Metrics | Latency, message complexity, robustness, scalability |

---

## Why This Matters

Leader election is at the heart of real-world distributed systems — Kubernetes uses Raft for control plane leader election, ZooKeeper uses a Zab-based protocol, and etcd relies on Raft consensus. Understanding how these algorithms behave under failure is critical for building reliable infrastructure.

This research provides empirical evidence for algorithm selection based on real failure scenarios rather than theoretical best-case assumptions.

---

## Author

**Prerana Puttaswamy**  
MS Computer Science, California State University, Long Beach  
[GitHub](https://github.com/prerana-puttaswamy) | [LinkedIn](https://www.linkedin.com/in/prerana-puttaswamy-a07836224/) | [Portfolio](https://preranap.vercel.app)
