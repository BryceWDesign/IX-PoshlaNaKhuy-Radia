# Shielding and Housing Options  
**IX-RadiaCore — Radiation-Resistant and EMI-Safe Housing Strategies**

This document outlines real-world materials and design methods to enhance the **passive protection** of the IX-RadiaCore system.

Proper shielding protects:
- Internal electronics from radiation damage  
- Operators from secondary emission  
- Nearby platforms from EMI/RF leakage  
- Filters and sensitive parts from thermal or particle degradation

---

## 🧱 1. Shielding Purpose by Threat Type

| Threat | Risk | Shielding Strategy |
|--------|------|--------------------|
| Ionizing Radiation | Component damage | Leaded polymer, borated HDPE, tungsten-infused casing |
| Electromagnetic Interference (EMI) | Signal corruption | Copper mesh wrap, Faraday cage insert |
| Thermal Overload | Component fatigue | Ceramic coating, vented aluminum alloy |
| Acoustic Harmonics | Feedback or resonance | Foam dampeners, internal baffles |

---

## 🪨 2. Materials for Gamma/Neutron Shielding

| Material | Use Case | Notes |
|----------|----------|-------|
| Borated Polyethylene | Neutron absorption | Lightweight, easy to shape |
| Leaded Acrylic or Polymer Sheet | Gamma attenuation | Transparent, moldable |
| Tungsten Plates (1–2mm) | High-density gamma barrier | Machinable but heavier |
| Concrete Micro-Bricks (Static Unit Only) | Radiation-safe fixed housing | Too heavy for aerial use |

---

## 🛡️ 3. EMI Shielding Methods

### External Wrap
- Fine copper mesh (0.1–0.3 mm) adhered between inner and outer shell
- Grounded via 1-point junction to prevent loop currents

### Internal Box Shielding
- Faraday box or partial cage for:
  - MCU board
  - HV driver
  - RF modulator

> 🧠 EMI control is critical when Tesla harmonics and HV pulse bursts coexist in close proximity.

---

## 🏗️ 4. Housing Structure Options

### Material Options:
| Material | Application |
|----------|-------------|
| ABS | Light, impact-resistant, easy to fabricate |
| Polycarbonate | Higher temp tolerance, UV resistant |
| Aluminum (6061 or 7075) | Great EMI barrier, conductive, machinable |
| Carbon Fiber | Lightest, but must be paired with EMI liner due to conductivity issues |

### Assembly Methods:
- Rivet frame with shock mounts  
- Snap-fit modular shell  
- Hinged service access door with EMI gasket  
- Rear-mounted fan slots or side passive venting

---

## ♻️ 5. Radiation-Tolerant Fasteners and Insulation

| Part | Recommended Material |
|------|----------------------|
| Screws / Bolts | Stainless steel or ceramic-coated steel |
| Gaskets | Silicone with EMI mesh or borated rubber |
| Insulation | PTFE (Teflon), aerogel layer (optional), fiberglass tape |
| Cable shielding | Braided copper or silver-coated mesh sleeve |

---

## 🔄 6. Maintenance Notes

- Inspect all shielding materials **every 10–15 deployments**
- Replace foam dampers if deformation exceeds 10%  
- Check leaded or borated panels for **cracking or delamination**  
- Clean external mesh with alcohol only — no abrasives

---

## ✅ Summary

Shielding and housing strategies allow IX-RadiaCore to survive and operate in:
- High EM field zones  
- Gamma or neutron-loaded fallout clouds  
- Mobile or fixed installations  
- Remote or extreme environments

All materials listed are **COTS**, **non-military**, and **globally available**.

---

**Next File:** `/hardware/Sensor-and-Telemetry-Options.md`  
→ Covers field diagnostics, wireless telemetry, and sensor array integration

**© 2025 Bryce Wooster — Contain, Protect, Perform**
