# Case Study: Global Telemetry Ingestion Plane

## 🚀 The Challenge
Designing a system to ingest petabytes of telemetry from millions of endpoints with a requirement for < 5s "freshness" (time from event to queryability).

## 🏗️ Architecture Choice: Lambda vs. Kappa
- **Decision:** I opted for a **Kappa Architecture** using a unified stream processing layer.
- **Why:** To reduce the operational complexity of maintaining separate batch and speed layers, ensuring consistent logic for both real-time alerts and historical analysis.

## ⚖️ Trade-offs & Bottlenecks
1. **Consistency vs. Availability:** In a global plane, we prioritize **High Availability (AP)**. Occasional duplicate telemetry is acceptable, but blocking ingestion during a network partition is not.
2. **Partitioning Strategy:** Implemented **Shard-Key based partitioning** on `TenantID` to prevent "Hot Partitions" during bursty traffic from large customers.

## 🛡️ Resilience
Utilized **Circuit Breakers** and **Dead Letter Queues (DLQ)** at the ingestion gateway to handle downstream sink failures without losing data.
