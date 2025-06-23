# NUMA (Non-Uniform Memory Access)

## Overview

NUMA is a memory design architecture used in multiprocessor systems where memory access time depends on the memory location relative to the processor. This design improves scalability and performance by localizing memory access.

---

## Key Concepts

- **NUMA Node:** A grouping of CPUs and local memory.
- **Local Memory Access:** Fast, as it’s on the same node as the CPU.
- **Remote Memory Access:** Slower, involves inter-node communication.
- **NUMA-aware Applications:** Optimize memory allocation for better performance.

---

## Example: 2 NUMA Nodes

| Node | CPUs        | Memory     |
|------|-------------|------------|
| 0    | CPU0–CPU7   | 64 GB RAM  |
| 1    | CPU8–CPU15  | 64 GB RAM  |

- CPU2 accessing Node 0 memory → **Fast**
- CPU2 accessing Node 1 memory → **Slower**

---

## Importance of NUMA

- Reduces memory latency.
- Improves throughput for memory-intensive workloads.
- Crucial for:
  - High-Frequency Trading (HFT)
  - High-Performance Computing (HPC)
  - Databases and virtualized environments

---

## Linux Tools for NUMA

| Tool         | Description                                   |
|--------------|-----------------------------------------------|
| `lscpu`      | Displays NUMA nodes and CPU topology          |
| `numactl`    | Binds processes/memory to specific NUMA nodes |
| `numastat`   | Shows NUMA memory allocation stats            |
| `hwloc-ls`   | Visualizes system topology                    |

---

## Best Practices

- Keep memory access **local** when possible.
- Use `numactl` to pin CPU and memory for performance-sensitive tasks.
- Monitor with `numastat` and `perf` to find bottlenecks.
- Consider `taskset` for CPU affinity, though it doesn’t manage memory locality.

---

## References

- [Linux NUMA Guide](https://www.kernel.org/doc/Documentation/vm/numa)
- `man numactl`, `man numastat`, `man taskset`
- `hwloc` project: https://www.open-mpi.org/projects/hwloc/

