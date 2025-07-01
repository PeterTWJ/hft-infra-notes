# ✅ HFT Spare Machine and Component Pre-Check Guide

In high-frequency trading (HFT), spare servers and components must be **pre-validated** to avoid any risk of latency regressions, performance jitter, or failure during critical market hours. This guide outlines a deterministic process for verifying spare assets before they are approved for deployment.

---

## 🖥️ 1. Bare-Metal Server Burn-In Checklist

### 🔧 Firmware and Configuration
- [ ] BIOS, BMC, NIC, and storage firmware updated to golden baseline
- [ ] BIOS configured for low-latency:
  - C-states disabled
  - Hyper-Threading disabled
  - Turbo disabled (if required)
- [ ] Confirm NUMA layout with `lstopo` or `numactl`
- [ ] PXE boot verified and OS autoprovisioning successful

### 🔍 Stress & Health Tests
- [ ] Run `memtest86+` or `stress-ng` for memory and CPU stability
- [ ] Burn-in stress for 24–72 hours using `sysbench` or equivalent
- [ ] Monitor thermal behavior and fan response
- [ ] Check system logs for hardware or kernel-level errors

---

## 🌐 2. NIC and Optical Transceiver Validation

### 🧪 NIC Testing
- [ ] Link up at expected speed (e.g. 10/25/100GbE)
- [ ] Verify IRQ assignment and CPU affinity (`/proc/interrupts`)
- [ ] Run latency benchmarks (`pktgen`, `moongen`, `iperf`)
- [ ] Confirm correct driver and firmware loaded with `ethtool`

### 🔦 Optics and Cabling
- [ ] Clean and inspect fiber and QSFP/SFP ends
- [ ] Run loopback test to verify signal quality
- [ ] Check DDM readouts (temp, TX/RX power) using `ethtool`
- [ ] Record transceiver model and firmware version

---

## 🧰 3. Spare Component Testing

### 🔹 RAM
- [ ] Run `memtester` under load
- [ ] Check for ECC errors in system logs

### 🔹 SSDs
- [ ] Secure-wipe disks
- [ ] Check `smartctl` health attributes

### 🔹 CPUs
- [ ] Validate model, microcode version, and thermal response
- [ ] Benchmark single-core and multi-core consistency

### 🔹 Fans & PSUs
- [ ] Run in chassis under load
- [ ] Check voltage stability and RPM feedback

---

## 📦 4. Inventory and Asset Logging

- [ ] Label all validated parts with barcodes or QR codes
- [ ] Log serial numbers, firmware versions, and validation status
- [ ] Store spares in a clean, organized, access-controlled area
- [ ] Update DCIM (e.g., NetBox) or internal asset management DB

---

## 🛠️ 5. Standardized Burn-In Scripts

- PXE boot into a burn-in image
- Run scripted checks:
  - BIOS/firmware validation
  - Network throughput and latency
  - CPU/NIC/IRQ affinity checks
- Output logs into centralized monitoring system or asset database

---

## 🚦 Final Validation Before Deployment

- [ ] Re-test if spare has been idle >30 days
- [ ] Confirm MAC/IP assignment is correct
- [ ] Ensure cable routes match latency-sensitive layout
- [ ] Re-clean optics before insertion into production system

---

## ✅ Goals of HFT Spare Validation

| Objective         | Description                                       |
|------------------|---------------------------------------------------|
| **Determinism**   | Ensure predictable, error-free deployment         |
| **Performance**   | Avoid hidden latency from BIOS, IRQ, or optics    |
| **Traceability**  | All assets are logged, labeled, and auditable     |
| **Zero Surprises**| No uncertainty during trading or market open      |

> "In HFT, uncertainty is risk. A properly validated spare is a weapon, not a liability."