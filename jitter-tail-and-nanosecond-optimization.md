# Jitter, Tail Latency, and Nanosecond Optimization

## Jitter
- Variation in latency between operations.
- High jitter = unpredictable timing.
- Matters for systems where every microsecond/nanosecond counts (e.g., HFT).

## Tail Latency
- The slowest response times (e.g., 99th/99.9th percentile latency).
- Critical for HFT: rare slow responses can cause missed trades or increased risk.
- Not just average latency—focus on worst cases.

## Nanosecond Optimization
- Tuning hardware and software for latency at the nanosecond scale.
- Techniques:
  - Custom NICs, hardware timestamping
  - Kernel bypass (DPDK, Solarflare, Onload)
  - CPU pinning, RT kernels, BIOS tuning
  - Disabling interrupts, using FPGAs

## How They Relate
- Reducing jitter and tail latency is the **goal** of nanosecond optimization.
- All three are crucial for ultra-low-latency, deterministic systems (like HFT).

---

**In summary:**  
- Jitter = inconsistency  
- Tail latency = rare, worst-case slowness  
- Nanosecond optimization = minimizing both for maximum speed and predictability