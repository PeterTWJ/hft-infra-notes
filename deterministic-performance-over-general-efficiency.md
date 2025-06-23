# Deterministic Performance over General Efficiency

## Deterministic Performance
- Consistent, predictable timing (low jitter).
- Prioritizes worst-case guarantees over resource use.
- Example: HFT, robotics, real-time control.

## General Efficiency
- Maximizing average throughput and resource utilization.
- Accepts occasional delays (higher jitter) for better overall output.
- Example: Cloud, web, batch processing.

## Why Choose Deterministic Performance?
- In HFT, a single slow operation can be more costly than missing throughput.
- Predictable systems may "waste" resources to guarantee response time.

## Techniques
- CPU/core pinning
- Disable CPU power saving
- Avoid batching/background tasks
- Real-time OS and kernel tuning
- Polling over interrupts

## Trade-off Table

| Aspect      | Deterministic         | Efficiency        |
|-------------|-----------------------|-------------------|
| Focus       | Consistency, low jitter | Max throughput   |
| Resource    | Often underused       | Fully utilized    |
| Use Case    | HFT, RT systems       | Cloud, web, batch |

---

**Summary:**  
- Choose deterministic performance for applications where timing **guarantees** matter more than maximum output.