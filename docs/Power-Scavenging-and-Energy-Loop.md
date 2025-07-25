# Power Scavenging and Energy Loop  
**IX-RadiaCore — Radiation-Driven Self-Powering Architecture**

This document outlines how the IX-RadiaCore system:
1. Scavenges energy from ambient radiation and EM field behavior  
2. Stores and regulates that power  
3. Routes energy to operational subsystems  
4. Minimizes reliance on external power sources

---

## ⚡ 1. Why Energy Scavenging Works

In radiation-contaminated environments:
- Ambient EM fluctuations, ion collisions, and static charge gradients are **stronger than normal**
- These interactions **induce microcurrents** in conductive media
- This field activity can be captured using **non-linear dielectric and semi-liquid cells**

---

## 🧪 2. Primary Energy Capture Device: ZeroCell

### Structure:
- **Core:** GaInSn (Gallium-Indium-Tin eutectic)
- **Electrodes:** Gold-plated copper or aluminum
- **Container:** Glass or PTFE, vacuum-sealed

### Behavior:
- Functions as a **liquid metal rectifier**
- Absorbs EM fluctuations and ion field transitions
- Generates continuous **low-voltage DC (~1–2V per cell)** under exposure

> 📘 Real-world precedent: Electret batteries, ambient energy scavengers, nuclear ion stirrer harvesters (DOE trials)

---

## 🔋 3. Storage Bank: Hybrid Capacitor Stack

### Components:
- Graphene ultracapacitors (2.7V, 500–3000F)
- Charge balancer IC
- Boost/Buck DC converter

### Function:
- Smooths raw DC from ZeroCell and HV grid feedback
- Converts power to:
  - 3.3V (logic)
  - 5V (audio systems)
  - 12V (coil drivers)
  - 24–48V (plasma curtain or fans)

> ⚠️ Capacitor arrays preferred over batteries due to radiation tolerance and cycle lifespan

---

## 🔄 4. Energy Input Sources

| Source | Output Type | Description |
|--------|-------------|-------------|
| ZeroCell | 1–2V DC | Passive, always-on, EM + radiation harvesting |
| HV Return Line | 2–20V DC (converted) | Recovers wasted corona charge from IDA |
| Harmonic Coil | AC ripple (~0.3A) | Secondary induction into buffer |
| External DC | Optional (12–24V) | Used for bootstrapping if needed |

---

## ⚙️ 5. Subsystem Power Routing

| Subsystem         | Voltage | Power Demand (typical) |
|------------------|---------|-------------------------|
| Ion Draw Array   | 20–40kV (low current) | ~1–5W (with efficient HV source) |
| Resonance Sink   | 12V PWM | ~3–6W peak |
| EM-Acoustic Driver | 5–12V | ~4W burst load |
| Filters & Fans   | 12V | ~1–2W |
| Plasma Curtain   | 24–48V (optional) | ~15–20W (duty cycle modulated) |
| MCU Control Logic | 3.3V or 5V | <0.5W |

All routed through:
- **Smart DC Bus**
- **Current-limited fuse matrix**
- **Optional microcontroller-based load balancing**

---

## 🔌 6. Realistic Output Profile

| Radiation Zone | Scavenged Power Output |
|----------------|------------------------|
| Low (1–10 μSv/h) | ~2–4W total | Enough to sustain logic, sensors, basic HV |
| Medium (10–50 μSv/h) | ~8–15W | Full system active, low plasma use |
| High (50–100+ μSv/h) | 20–40W | Sustains entire system w/ plasma curtain, fans |

---

## 🛑 Failover Strategy

- If scavenged power drops:
  - Switches to **low-power draw mode**
  - Disables plasma or acoustic system
  - Prioritizes filter and IDA
- External port available for field recharging or solar input if needed

---

## ✅ Summary

IX-RadiaCore converts radiation field conditions into usable power using:
- GaInSn-based ZeroCells
- Inductive field capture
- High-efficiency ultracapacitor banks

This gives the system **semi-infinite run time** in contaminated zones without fuel, batteries, or grid power.

---

**Next File:** `/hardware/External-Mounting-and-Platform-Adaptation.md`  
→ How to attach the unit to drones, vehicles, aircraft, or fixed posts

**© 2025 Bryce Wooster — Fuel by Fallout, Powered by the Problem**
