# 🧠 HFT Infrastructure Engineering Notes

Welcome to my personal knowledge base focused on **ultra-low-latency infrastructure**, system tuning, and automation techniques relevant to high-frequency trading (HFT) environments.

---

## 👋 Background

I previously worked in a **FAANG-scale data center**, where the focus was on:
- Scalable automation
- Resilient system architecture
- Cloud-oriented infrastructure operations

These experiences gave me a strong foundation in managing systems at scale.

However, **infrastructure for HFT** has a different set of priorities:
- **Determinism over throughput**
- **Bare-metal over virtualized environments**
- **Nanosecond precision over general availability**

This repository documents how I’ve adapted my infrastructure thinking and skills toward the **demands of HFT systems**.

---

## 🔍 FAANG vs HFT Infrastructure Focus

| Area                        | FAANG Focus                          | HFT Focus                                |
|-----------------------------|---------------------------------------|-------------------------------------------|
| Performance Optimization    | Throughput, scalability               | Determinism, ultra-low latency            |
| Power Management            | Efficiency (Turbo/C-states enabled)   | Consistency (Turbo/C-states disabled)     |
| CPU Usage                   | Shared and virtualized cores          | Isolated physical cores (`isolcpus`, etc.)|
| Time Synchronization        | Millisecond-level NTP                 | Nanosecond-level PTP + PHC                |
| OS Tuning                   | General-purpose defaults              | Kernel bypass, IRQ pinning, hugepages     |
| Provisioning Philosophy     | Cloud images, container-first         | PXE boot, bare-metal automation           |

---

## 📂 Repo Structure

```text
hft-infra-notes/
├── networking/         # Kernel bypass, NIC tuning, RPS/XPS
├── system-tuning/      # BIOS, C-states, CPU pinning
├── provisioning/       # PXE boot, iPXE, Kickstart, WinPE
├── time-sync/          # Chrony, PTP, PHC tuning
├── scripts/            # Bash, PowerShell, Ansible snippets
└── README.md
