# Hardware Control Over Abstraction

## What is Abstraction?
- Layers (OS, middleware, VMs) that hide hardware details, making software easier to build and portable.

## What is Hardware Control?
- Direct management and tuning of hardware—bypassing abstractions for maximum performance and determinism.

## Why Choose Hardware Control?
- **Low latency & determinism:** Avoid unpredictable delays from OS, drivers, VMs.
- **Max performance:** Tune BIOS, NICs, CPUs for the lowest possible latency.
- **Dedicated resources:** No noisy neighbors or shared contention.

## Examples (HFT/Low-Latency)
- Kernel bypass (DPDK, Solarflare)
- CPU core pinning, disabling SMT and power saving
- Custom BIOS/UEFI and FPGA/NIC programming

## Trade-Offs

| Aspect      | Hardware Control     | Abstraction         |
|-------------|---------------------|---------------------|
| Latency     | Minimum, deterministic | Variable         |
| Flexibility | Low (hardware-specific) | High (portable)  |
| Dev Speed   | Slow, complex        | Fast, easy         |

---

**Summary:**  
Choose hardware control when **every microsecond or nanosecond counts** (HFT, real-time, embedded). Use abstraction for ease and portability in general applications.