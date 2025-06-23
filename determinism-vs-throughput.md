# Determinism vs Throughput

## Determinism
- Predictable, consistent response times (low jitter).
- Essential for latency-sensitive tasks like HFT.
- Often requires limiting parallelism, pinning resources, and disabling non-essential services.

## Throughput
- Maximizing the total amount of work done per second (high requests/sec).
- Priority in large-scale, non-real-time systems (web, databases).
- Achieved by maximizing resource use, batching, and parallel processing.

## Trade-off

- **Determinism:** Sacrifices some throughput for predictability.
- **Throughput:** May introduce unpredictable latency to maximize work.

| Aspect       | Determinism                | Throughput               |
|--------------|----------------------------|--------------------------|
| Focus        | Low jitter, consistency    | Max work per second      |
| Use Case     | HFT, real-time control     | Web, batch, analytics    |
| Tuning       | CPU pinning, RT kernel     | MT, batching, full load  |
| Trade-off    | Lower capacity possible    | More latency variation   |

---

**In short:**  
- **HFT** prioritizes determinism.
- **Web-scale** systems usually prioritize throughput.