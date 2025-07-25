# EM Surge Protection and Hardening  
**IX-RadiaCore — EMP-Tolerant, Tesla-Compatible, Radiation-Hardened Design Principles**

This document defines real-world strategies to protect the IX-RadiaCore system against:

- EMP-like field spikes (non-nuclear)  
- Tesla coil feedback and field oscillations  
- Localized field collapse events (from plasma, lightning, or ion traps)  
- Radiation-induced failure of semiconductors and analog components

---

## ⚡ 1. Threat Models

| Threat | Description | Defense |
|--------|-------------|---------|
| HV Pulseback | Spike from disrupted coil collapse | Snubber, TVS, MOVs |
| EMP Field Burst | Rapid voltage induction via E field | Faraday shell, in-line clamping |
| Radiation-Induced Latchup | High-energy particles lock logic states | IC selection + filtering |
| RF Interference | Tesla harmonics bleeding into control path | Shielding, choke isolation |

---

## 🧰 2. Surge Suppression Stack

### A. Input Power Protection

| Component | Spec | Notes |
|----------|------|-------|
| Polyfuse (resettable) | 1.5A–2.5A | Protects from overdraw or shorts |
| MOV (Metal Oxide Varistor) | 14V–18V clamp | Absorbs large spikes |
| TVS Diode (Bidirectional) | 12V, 400W+ | For fast spike clamping |
| Ferrite Beads | 100–300 Ω @ 100 MHz | EMI suppression on VCC lines |

---

### B. Logic-Level and MCU Protection

- Add **0.1uF decoupling caps** close to every IC VCC pin  
- Use **Schottky diodes** on signal inputs (to VCC and GND)  
- Install **series resistors (100–330Ω)** on I/O pins  
- Ground planes below all MCU layers  
- Use **hardware watchdog timers** for latchup recovery

---

## 🧲 3. RF and EM Field Isolation

| Component | Location | Purpose |
|----------|----------|---------|
| Mu-metal or soft iron sheet | Around coil and HV stages | Absorbs magnetic spikes |
| Copper or aluminum mesh wrap | Around MCU enclosure | EMI Faraday isolation |
| Shielded twisted pair cabling | Between MCU and sensors | Cancels common-mode RF |

---

## 🧪 4. Radiation-Resistant Component Selection

### A. Passive Components:
- Use ceramic capacitors (NP0/C0G) — stable under radiation  
- Metal film resistors > carbon film for lower drift  
- Avoid electrolytic caps near HV or heat zones

### B. Active Components:
- Choose MCUs with known tolerance (STM32F103, RP2040, etc.)  
- Avoid high-density FPGAs or BGA chips unless space-rated  
- Use discrete logic where possible (74HC, 4000 series)

---

## 🔄 5. Recovery and Fallback Design

- Include **manual reset button** and auto-reboot circuit  
- Store **last-good config on EEPROM** or SD  
- Log all telemetry and alerts locally during blackout events  
- Bypass or “limp mode” logic: allow fallback to passive filtration if MCU dies

---

## 🛑 6. Grounding Best Practices

- Central star ground near coil driver  
- Isolate analog/digital grounds if separate MCU domains used  
- Use **ground lugs on metal frame + shield mesh**  
- Never float ground near HV unless designed as differential rail

---

## ✅ Summary

Rad-hard design doesn’t require space-grade components — just:
- Smart layout  
- Correct suppression parts  
- Robust fallback logic  
- Real-world shielding strategies

> ⚙️ If the system survives *one* hard field spike and reboots — it’s done its job.

---

**Next File:** `/hardware/Radiation-Capture-Mechanism.md`  
→ Covers physical and electrostatic capture principles for airborne radioactive particles

**© 2025 Bryce Wooster — The Field May Surge, But This Core Holds**
