# IX-RadiaCore — Bill of Materials (BOM)

This document provides a complete parts list for building the IX-RadiaCore radiation extraction and self-powering unit. All components are **real, purchasable**, and selected for **open-source accessibility** and **modular buildability**.

---

## 📦 Core Subsystem: Ion Draw Array (IDA)

| Qty | Component                        | Description                                      | Source / Notes                   |
|-----|----------------------------------|--------------------------------------------------|----------------------------------|
| 2   | Stainless Steel Mesh Panels      | Electrostatic grid, 50–200 mesh                  | Any lab supply or Amazon         |
| 1   | High Voltage Power Supply (20–40kV) | Compact HV DC supply, ~1–5mA output           | eBay, SparkFun, AliExpress       |
| 4   | PTFE Insulation Standoffs        | Dielectric support for HV grid                   | McMaster-Carr, Digikey           |
| 1   | Voltage Regulator Module         | HV control (0–40kV output scaling)               | Available via HV control kits    |

---

## 🧲 Tesla Harmonic Convergence Module (RSC)

| Qty | Component                        | Description                                      | Source / Notes                   |
|-----|----------------------------------|--------------------------------------------------|----------------------------------|
| 1   | Copper Bifilar Coil (Custom Wound) | 20–40 turns, 16 AWG, insulated                 | Handmade or order via coil labs  |
| 1   | Ferrite Core Ring                | Toroidal or rod form for field shaping          | TDK, Fair-Rite, Digikey          |
| 1   | Tesla Frequency Driver Circuit   | 3–phase harmonic output, 3-6-9 logic compatible  | Custom or function gen + amp     |
| 1   | Harmonic Pulse Generator         | Microcontroller-controlled burst driver         | Arduino Nano or STM32 preferred  |

---

## ⚡ Ambient Energy Capture + Storage (APL)

| Qty | Component                        | Description                                      | Source / Notes                   |
|-----|----------------------------------|--------------------------------------------------|----------------------------------|
| 1   | GaInSn Liquid Metal Core Cell    | For ZeroCell variant harvesting                  | Purchase from LiquidMetalHub     |
| 2   | Graphene Supercapacitor (2.7V, 500F) | Energy buffer bank                         | Maxwell or Kilowatt Labs         |
| 1   | Capacitor Charge Balancer        | For safe ultracap balancing                     | Common in ultracap arrays        |
| 1   | Boost/Buck Converter (10–50V DC) | Auto adjusts output for external systems        | Adafruit or Pololu               |

---

## 🔊 EM-Acoustic Disruptor Module (EAD)

| Qty | Component                        | Description                                      | Source / Notes                   |
|-----|----------------------------------|--------------------------------------------------|----------------------------------|
| 1   | High-Frequency Acoustic Driver   | 20–80 kHz ultrasonic or magnetostrictive         | Murata or ultrasonic module sets |
| 1   | Tesla Sideband Modulator         | For harmonic sweep overlay                       | Custom circuit or op-amp config  |
| 1   | Pulse Trigger Circuit            | For microsecond-range bursts                     | 555 timer variant or STM32       |

---

## 🧼 Filter Containment Stack (FCS)

| Qty | Component                        | Description                                      | Source / Notes                   |
|-----|----------------------------------|--------------------------------------------------|----------------------------------|
| 1   | HEPA Filter Sheet (Mini Size)    | Initial particulate trap layer                   | 3M, Honeywell, or salvaged       |
| 1   | Zeolite Mineral Cartridge        | Cesium + strontium absorber                      | Aquarium supply or lab grade     |
| 1   | Boron-Carbon Fiber Mesh          | Neutron-moderating mesh layer                    | Nuclear-safe equipment suppliers |
| 1   | Acoustic Foam Baffle             | Final layer, deadens harmonic noise              | Soundproofing grade, 1–2 cm thick|
| 1   | Snap-Fit Casing or Tube Body     | Holds stack together with vented intake ports    | 3D printed or laser-cut acrylic  |

---

## 🔗 Structural + Auxiliary

| Qty | Component                        | Description                                      | Source / Notes                   |
|-----|----------------------------------|--------------------------------------------------|----------------------------------|
| 1   | Casing Chassis (38×38×18cm)      | Shell made of ABS, aluminum, or composite        | Custom build, CNC, or 3D print   |
| 1   | EMI Shielding Liner              | Interior wrap for HV and harmonic systems        | Mu-metal foil or copper mesh     |
| 1   | Cooling Fan or Passive Vents     | Optional airflow to assist particle flow         | 12V fan or mesh intake            |
| 1   | Mounting Rail Bracket            | Universal bottom-mount system                    | Aluminum extrusion rail + bolts  |

---

## 🧰 Tooling & Assembly Aids

| Qty | Item                             | Description                                      |
|-----|----------------------------------|--------------------------------------------------|
| –   | 3D Printer / CNC Router          | For casing and precision cut panels              |
| –   | Soldering Station + Multimeter   | Basic assembly + diagnostic                      |
| –   | Epoxy or Thermal Paste           | For heat contact bonding and insulation          |

---

### Estimated Total BOM Cost (Prototype Unit):
- **$280 – $540 USD** depending on sourcing
- All components are **non-restricted, non-dual-use**, and commercially available

---

## Disclaimer

This BOM is curated for **maximum real-world accessibility**. No proprietary or restricted items are used.  
Substitutions are allowed where component function is maintained.

---

**Next File:** `/hardware/Build-Instructions.md`  
→ Full step-by-step guide to construct IX-RadiaCore

**© 2025 Bryce Wooster – All Rights Reserved under Humanitarian License**
