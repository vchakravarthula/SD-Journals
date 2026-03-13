# 🌐 System Design & Architecture Journal

A technical collection of high-level design (HLD) patterns and case studies for planet-scale systems. This repository documents my approach to scalability, availability, and distributed data management.

## 🏗️ Case Studies
### 1. Global Telemetry Ingestion Plane
- **Focus:** Scalability & Observability.
- **Problem:** Handling petabytes of telemetry with < 5s retrieval latency.
- **Solution:** Distributed ingestion using partitioned message queues and optimized KQL storage layers.

### 2. Rate Limiting for Multi-tenant APIs
- **Focus:** Security & Fair-usage.
- **Strategy:** Token Bucket algorithm implemented at the API Gateway layer.
