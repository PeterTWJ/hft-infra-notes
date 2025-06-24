# Adjusting Interrupt Coalescing for Windows

## What is it?
- Known as **Interrupt Moderation** or **Interrupt Moderation Rate** in Windows NIC properties.
- Lowering/disabling it reduces latency, increases CPU usage.

## How to Adjust

1. **Open Device Manager**
   - `Win + X` → Device Manager

2. **Find Network Adapter**
   - Expand **Network adapters**
   - Right-click your NIC → **Properties**

3. **Advanced Tab**
   - Go to **Advanced**
   - Look for **Interrupt Moderation** or **Interrupt Moderation Rate**

4. **Set to Lowest/Disabled**
   - Set **Interrupt Moderation** = **Disabled**
   - Set **Interrupt Moderation Rate** = **Off** or **Low**

5. **Apply and Reboot**

## Related Settings
- **Receive/Transmit Buffers:** Lower for lower latency (test for your use case)
- **Receive Side Scaling (RSS):** Sometimes disabling can help, but test

## Caution
- Not available on all NICs.
- Higher CPU usage when disabled.
- Always test for your specific hardware and workload.

---

**Summary:**  
Lower or disable Interrupt Moderation in Windows NIC settings for the lowest latency and jitter—ideal for HFT, real-time, and gaming, but watch CPU load!
