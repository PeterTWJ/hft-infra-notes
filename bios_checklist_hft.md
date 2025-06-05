# 🧬 HFT BIOS Tuning Checklist

> Manual checklist for BIOS/UEFI configuration on HFT-grade servers (e.g., Supermicro, Dell, HP).  
> The goal is to **maximize determinism** and **minimize latency/jitter** in performance-critical environments.

---

## 🔧 Power & Performance Settings

- [ ] **CPU Power State**: `Maximum Performance` or equivalent  
- [ ] **Enhanced Intel SpeedStep (EIST)**: `Disabled`  
- [ ] **Intel Turbo Boost**: `Disabled`  
- [ ] **C-States (C1E, C3, C6)**: `Disabled`  
- [ ] **Package C-State Limit**: `C0` or `Disabled`  
- [ ] **CPU Thermal Throttling**: `Disabled` (if thermally safe)  
- [ ] **Hardware Prefetchers (L1/L2)**: `Enabled` (if deterministic behavior maintained)  
- [ ] **Hyper-Threading (SMT)**: `Disabled` (preferred for predictable performance)  

---

## 🧠 Memory Settings

- [ ] **NUMA Nodes per Socket**: `1`  
- [ ] **Memory Interleaving**: `Enabled (Performance)`  
- [ ] **Memory Scrubbing / Patrol Scrub**: `Disabled` (if not required for ECC maintenance)  

---

## ⏱️ Timers & Virtualization

- [ ] **HPET (High Precision Event Timer)**: `Enabled`  
- [ ] **TSC as Time Source**: `Enabled (Preferred)`  
- [ ] **VT-x / VT-d**: `Disabled` (unless using passthrough with kernel bypass tech)  

---

## 📡 Network Considerations

- [ ] **PXE Boot**: `Enabled` (if provisioning via PXE)  
- [ ] **Onboard NIC Option ROMs**: `Enabled` (only for required ports)  

---

## 🧪 Debug & Misc

- [ ] **Watchdog Timer**: `Disabled`  
- [ ] **Serial Port**: `Disabled` (unless needed)  
- [ ] **USB Legacy Support**: `Disabled`  
- [ ] **BIOS POST Time**: Set to `Minimal` or `Fast Boot`  
- [ ] **Fan Speed Policy**: `Max Performance` or fixed PWM for deterministic thermals  
- [ ] **BIOS Update Lock**: `Enabled` (optional; for immutability)

---

## 💡 Notes

- Always verify changes via `dmidecode`, `lscpu`, `tuned-adm`, or vendor IPMI tools post-boot.
- BIOS settings may vary slightly by manufacturer (Supermicro, Dell iDRAC, HP iLO, etc.)
- Consider documenting the BIOS version and profile checksum after tuning.
