# ✅ HFT Server Burn-In & Offline Diagnostic Checklist

Use this checklist to validate spare machines or components **before deployment**. All tests should be performed in a controlled environment, typically via **PXE boot into a burn-in image** or USB offline tools.

---

## 🔧 PXE Boot Provisioning

- [ ] PXE boot into burn-in Linux environment (e.g. Ubuntu Minimal, CentOS Live)
- [ ] Auto-mount diagnostic scripts and logging tools
- [ ] Verify DHCP/MAC mapping and correct kickstart/init config loaded
- [ ] Log PXE timestamp and boot time for latency tracking

---

## 🖥️ Server Firmware & BIOS

- [ ] Check and log BIOS version (should match golden baseline)
- [ ] Check and log BMC/iDRAC firmware version
- [ ] Flash firmware (Dell: `FIRMIMG.D7`, Supermicro: `SUM`)
- [ ] Verify BIOS settings:
  - [ ] C-States: Disabled
  - [ ] Turbo Boost: Disabled
  - [ ] Hyper-Threading: Disabled
  - [ ] NUMA enabled, no interleaving
  - [ ] SR-IOV, VT-d (if required): Enabled
- [ ] Save BIOS config to file (if supported)

---

## 🧪 CPU / RAM Burn-In

- [ ] Run `stress-ng` or `sysbench` for 2–4 hours
- [ ] Run `memtest86+` or `memtester` for at least 2 passes
- [ ] Log CPU temps, frequency, fan curves
- [ ] Check dmesg/system logs for ECC or MCE errors

---

## 🌐 NIC & Networking Validation

- [ ] Check NIC firmware and driver (`ethtool -i`)
- [ ] Confirm link up at correct speed (10G/25G/40G/100G)
- [ ] Verify IRQ pinning and NUMA locality
- [ ] Run `pktgen`, `moongen`, or `iperf` (optional loopback or peer test)
- [ ] Validate SR-IOV or DPDK compatibility if required

---

## 🔦 Optics and Cabling

- [ ] Clean and inspect QSFP/SFP ends
- [ ] Run loopback test to verify signal integrity
- [ ] Read DDM data: TX/RX power, temperature, faults
- [ ] Log optic vendor, model, and firmware

---

## 🧰 Storage & SSDs

- [ ] Secure erase using vendor tool or `nvme format`
- [ ] Check SMART health (`smartctl -a`)
- [ ] Validate IOPS or throughput with `fio` (optional)
- [ ] Check for wear-level, reallocated sectors, or pending errors

---

## 🔋 Power, PSU, and Fan Checks

- [ ] Monitor live voltage and amperage draw (via IPMI/iDRAC)
- [ ] Check all fans operational and ramp under load
- [ ] Run PSU self-test (if vendor supports)
- [ ] Validate thermal shutdown threshold behavior

---

## 📁 Logging & Asset Registration

- [ ] Tag with hostname / serial number
- [ ] Save full system log bundle (dmesg, sensor, BIOS, BMC)
- [ ] Upload to asset DB or CMDB (e.g. Netbox)
- [ ] Label hardware as **Burned-in: ✅ Ready for Prod**

---

## 🧾 Optional Vendor Diagnostic Tools

### Dell
- [ ] Boot into Dell SupportAssist USB ISO for full diagnostics
- [ ] Run Lifecycle Controller (F10) and validate system health
- [ ] Export logs and service tag for RMA proof

### Supermicro
- [ ] Run Supermicro Update Manager (SUM) for firmware checks
- [ ] Use SuperDoctor or IPMICFG for sensor verification
- [ ] Pull and archive SEL and FRU logs

---

## ✅ Final Review Before Rack Deployment

- [ ] Confirm cabling plan and port map ready
- [ ] Match power budget and PDU availability
- [ ] Confirm MAC/IP are reserved and known to Netbox/DHCP
- [ ] Clean optics again before final insertion

---

> ✅ **Only deploy hardware that passes all checks without exceptions.**
> In HFT, uncertainty = risk. Determinism starts at the hardware layer.