# Adjusting Interrupt Coalescing with `ethtool -C`

## What is Interrupt Coalescing?
- NIC feature that reduces CPU interrupts by batching packet notifications.
- Reduces CPU load, but increases latency and jitter.

## Why Adjust?
- **Low-latency (HFT, trading):** Disable or minimize coalescing for lowest latency.
- **High-throughput:** Enable coalescing to reduce CPU usage.

## How To Set with `ethtool -C`
```bash
sudo ethtool -C <interface> rx-usecs <value> rx-frames <value>
