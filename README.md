# Leader Election under Crash-Recovery Fault Models

## Overview

This project simulates and evaluates leader election algorithms under realistic failure conditions in distributed systems. The study compares Bully, Ring, and Raft-style approaches, and introduces a Multi-Attribute leader election strategy.

## Key Contributions

* Simulated leader election under crash-recovery, network partitions, and message loss
* Compared Bully, Ring, and Raft algorithms across multiple performance metrics
* Designed a Multi-Attribute election algorithm using CPU load and battery-based scoring
* Built a discrete-event simulation system for reproducible experiments

## System Design

* Event-driven simulation engine with fault injection (crash, restart, partitions)
* Message bus modeling latency, jitter, and packet loss
* Node-level state machines implementing election protocols

## Metrics Evaluated

* Election latency (time to elect leader)
* Message overhead (communication cost)
* Success rate under faults
* System robustness under partitions

## Results

* Multi-Attribute algorithm achieved lowest re-election latency (~0.7s)
* Reduced message overhead compared to Bully while maintaining robustness
* Ring algorithm showed lower reliability under partitioned networks
* Demonstrated trade-offs between speed, cost, and fault tolerance

## Tech & Concepts

* Distributed Systems
* Fault Tolerance
* Simulation Systems
* Algorithms & Data Structures

## Author

Prerana Puttaswamy
