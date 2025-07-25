# Power Buffer & Ambient Scavenging  
**IX-RadiaCore — Autonomous Energy System for Field Operation**

This file defines how the system powers itself from ambient sources — including radiation, EM fields, and waste thermal gradients — and stores energy for onboard operations.

---

## 🔋 1. Why This Matters

Radiation isn't just dangerous — it's energy waiting to be harnessed.  
This system uses that fact.

Rather than depending on external battery swaps or limited solar trickles, the device:
- Pulls from environmental radiation (ionizing or EM)
- Reclaims waste heat and field stress
- Buffers into usable energy to power sensors, loops, fans, and logic boards

---

## ⚡ 2. Power Sources Overview

| Source | Description | Harvest Method |
|--------|-------------|----------------|
| Ambient Ionizing Radiation | Alpha/Beta/Gamma in air | Ion pair separation → capacitor plates |
| EM Field Saturation | RF/EM spillover near high-tension zones or radar sites | Rectenna array |
| High-Freq Tesla Coil Backloop | Field bounceback from Tesla choke | Inductive side-tap loop |
| Heat Differential | Environmental + internal heating | Peltier (TEC1-12706 or similar) |
| Manual Override (if needed) | USB-C or DC jack for startup | Optional — standard 5V in |

---

## 🔌 3. Power Harvesting Methods (Real-World)

### A. Capacitive Ion Collector

- Open air plate pair system
- Collects ion pairs formed by high-energy particles
- Energy bled into ultracapacitor bank
- Similar to passive nuclear particle energy experiments at universities (see Fukushima passive charge tests)

### B. Rectenna Grid (EM Harvester)

- 4x4 PCB rectenna array  
- Converts ambient RF (2.4GHz, 5GHz, GSM, radar) into DC trickle  
- Output regulated via ultra-low dropout buck module

### C. Inductive Back-Tap (Tesla Feedback)

- Secondary low-voltage coil wraps around Tesla choke core  
- Taps residual flux from oscillation cycles  
- Diode-protected, feeds supercapacitor → logic rails

---

## 🧊 4. Heat Scavenging (Thermoelectric Layer)

- One TEC1-12706 module placed beneath copper collector plate  
- Uses difference between warm airflow and grounded aluminum sink  
- Generates 1–2V @ ~200mA under delta T = 20°C  
- Boost-converted to 5V rail via XL6009

---

## 💾 5. Buffering System

| Component | Purpose | Model |
|-----------|---------|-------|
| 4x Supercapacitors | Primary short-term burst power | 2.7V 500F |
| Lithium Ion Pack (Optional) | Long-term buffer for off-hour ops | 3.7V 2200mAh |
| Ultra-LDO Regulator | Stable logic supply | AMS1117 or HT7333 |
| Schottky Diodes | Reverse path protection | SS14 or 1N5819 |

Capacitors store immediate harvest energy. Lithium (optional) used for night/sensor fallback logic.

---

## ⚙️ 6. Power Routing Logic

```plaintext
[Ambient Sources] → Boost Regulator → Cap Bank → Logic Bus (3.3V / 5V)  
                                        ↳ Tesla Oscillator Rail (via pulse MOSFET)  
                                        ↳ Fan & Actuator Rail  
Startup behavior:

Cold start triggers power scavenging loop first

Minimum 0.9V required to engage XL6009

Tesla output disabled until 3.0V available in buffer

🛠️ 7. Construction Notes
Copper mesh under drone belly (or case bottom) improves ion harvesting

Heat sink needs airflow — fan-assisted in stagnant conditions

EMI noise from Tesla loop must be shielded from rectenna grid — use copper foil trace barrier

✅ Summary
This device powers itself like a predator — not from food, but from the fear in the environment itself: radiation, static, noise, imbalance.

It lives off what the world fears — and uses it to clean the world instead.

Next File: /hardware/Field-Tuning-and-Resonance-Module.md
→ We’ll define how Tesla field oscillations are tuned, how frequency hopping works, and how harmonic convergence is real-time adapted.

© 2025 Bryce Wooster — Energy Is Everywhere. Let’s Use It to Undo the Damage.
