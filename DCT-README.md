# 🚀 HFT Infrastructure Study Notes for Data Center Technicians (DCT)

> A focused learning path and practical knowledge base for DCTs transitioning into High-Frequency Trading (HFT) infrastructure roles.

---

## 🧠 1. Foundations of HFT Infrastructure

- What is HFT? 
- Why latency matters?
- Core differences between FAANG and HFT infra
- Determinism vs throughput
- Jitter, tail latency, and nanosecond optimization

### Key Concepts
- Deterministic performance over general efficiency
- Hardware control over abstraction
- Precision engineering at every layer

---

## 🧬 2. Server Hardware Tuning (Hands-On)

### ✅ BIOS/UEFI Configuration
- **Disable**: 
  - C-States (C1E, C6)
  - Intel Turbo Boost
  - Hyper-Threading (SMT)
- **Enable**:
  - High Performance Power Mode
  - HPET (High Precision Event Timer)
  - NUMA-friendly settings

> 💡 Refer to vendor-specific BIOS guides (Supermicro, Dell iDRAC, HP iLO)

### ✅ Physical Hardware Tips
- PCIe slot placement matters for latency
- Ensure latest NIC firmware
- Use low-latency DIMMs
- Clean fiber tips before every reseat

---

## 🌐 3. Network Layer for Low Latency

### ✅ NIC Tuning
- Adjust interrupt coalescing (`ethtool -C`)
- RSS/RPS/XPS optimization
- Affinity pinning (IRQ to CPU core)
- Disable offloads as needed (TSO, LRO, GRO)

### ✅ Physical Layer Best Practices
- Clean fiber before insert
- Check with Visual Fault Locator (VFL)
- Use fixed speed negotiation where possible (avoid autoneg)

---

## 🔧 4. PXE Boot & Provisioning

### ✅ Tools to Know
- iPXE boot scripts
- Kickstart (`ks.cfg`) for automated Linux install
- WinPE + PowerShell scripting for Windows Server
- DHCP, TFTP, HTTP setup

### ✅ Common Tasks
- Troubleshooting PXE boot paths
- MAC address persistence after server swaps
- Handling Secure Boot/UEFI conflicts

---

## ⏱️ 5. Time Synchronization

### ✅ Why Time Matters
- Packet timestamp accuracy = trading accuracy
- PTP > NTP for nanosecond precision

### ✅ Tools
- `ptp4l`, `phc2sys`
- Chrony configuration
- Checking BIOS and PHC clock drift

---

## ⚙️ 6. Automation & Scripts (Lightweight)

### ✅ Recommended Tools
- `ipmitool`, `dmidecode`, `lscpu`, `ethtool`
- PowerShell: WMI for BIOS/NIC audit
- Bash: System info, tuning helpers

### ✅ Sample Use Cases
- Script to check C-state/Turbo status
- Audit NIC RX queues and interrupt bindings
- PXE installer with auto IPMI BIOS prep

---

## 🛠️ 7. Operations & SOPs (HFT-Focused)

### ✅ Typical Tasks
- Zero-downtime server swap with identical BIOS + MAC
- Handling packet drop or jitter alerts
- Clock drift response playbook
- Working with Linux Infra/Network teams on core pinning or BIOS validation

---

## 📈 Study Tips & Portfolio Suggestions

- Practice BIOS tuning in lab or home testbed
- Build a public or private GitHub repo with:
  - Markdown guides
  - Sample tuning scripts
  - Your own PXE boot notes
- Add tools/scripts you wrote for hardware checks or BIOS/UEFI audit

---

## 📚 Further Reading

- [Intel BIOS Optimization Guide for Low Latency](https://www.intel.com/content/www/us/en/programmable/documentation)
- [ethtool documentation](https://man7.org/linux/man-pages/man8/ethtool.8.html)
- [PTP (Precision Time Protocol) Basics](https://linuxptp.sourceforge.io/)
