# Power Scavenging and Boosting  
**IX-RadiaCore — Energy Harvesting and High-Voltage Amplification for Continuous Operation**

This subsystem enables the IX-RadiaCore to **run autonomously**, **scavenge ambient power**, and **boost voltage** to support high-energy operations like electrostatic draw, coil charge, and airflow maintenance.

---

## 🔌 1. Core Power Sources

### A. Ambient Scavenging — Primary
| Method | Source | Notes |
|--------|--------|-------|
| Tesla Bifilar Coil | EM field resonance | Tuned to ~7.83 Hz Schumann or local harmonics |
| PZT Stack | Acoustic → voltage | Converts drone or wind noise |
| Thermal Gradient TEG | Cold air vs device heat | Continuous, passive |
| Ambient RF | WiFi/Celltower/LoRa | Captured via broadband antenna loop |
| Capacitive Earth Gradient | Ground-coupled | If grounded (non-airborne config)

---

### B. Active Supplement — Optional
| Source | Integration | Notes |
|--------|-------------|-------|
| Small solar panel | 5V/500mA+ | Polycrystalline film preferred |
| Drone power tap | 12V-24V | If mounted directly under craft |
| Fuel cell (H2/O2) | External only | Not included in baseline unit

---

## 🔋 2. Primary Storage (Low Voltage Loop)

| Component | Spec |
|----------|------|
| Supercapacitor bank | 10–50F, 2.7V–5.5V total | Handles burst charge, no lithium required |
| Schottky diode OR-ing | <0.3V drop | Prevents backfeed across harvesters |
| Capacitor precharge circuit | 100Ω + relay | Avoids inrush damage to boost stack |

---

## ⚡ 3. High Voltage Boost Stack

Boost circuit generates **10–25 kV DC** to energize:
- Electrostatic draw plates  
- Ionic spray grid (optional)  
- Internal plasma scrubber  
- HV field oscillator (if present)

### Recommended Modules
| Type | Part | Notes |
|------|------|-------|
| CCFL inverter | Generic 12V → 20kV | Can be pulled from e-waste |
| Flyback converter | ZVS + TV flyback | More controllable, higher output |
| Boost converter | XL6009 or LT1073 | For logic-level power rail (5V/12V)

**Note**: Always include spark gap suppressor or TVS on HV output.

---

## 🌀 4. Tesla ZeroCell Integration

This enables self-sustaining charge maintenance via:
- Ambient harmonics (3/6/9 tuned coil)  
- Oscillating zero-potential waveform stabilization  
- Re-radiated harmonic pulses creating potential draw

**Basic Schematic Outline:**

[Field Coil] → [Tesla Tuning Cap] → [Resonant Receiver] → [Supercap] → [Boost Stack] → [HV Capture Grid]


- All stages grounded through isolated shielded bus  
- Optionally auto-tuned using low-power microcontroller (ESP32 or ATtiny85)

---

## 🧠 5. Voltage Monitoring and Power Logic

- INA219 for V/I telemetry  
- Undervoltage lockout (UVLO) switch — auto-shutoff at ~2.8V  
- Comparator logic for charge/release gating  
- All logic passively cooled via ambient flow channel

---

## 🛠️ 6. Physical Integration

- Mount scavengers on **peripheral frame** to avoid airflow obstruction  
- Boost modules and HV stacks **isolated via ceramic standoffs**  
- Tesla coil vertically stacked or off-axis for harmonic sync  
- Loops shielded via copper tape or braided wire sleeve

---

## ✅ Summary

The IX-RadiaCore becomes an autonomous unit by:
- Harnessing ambient, RF, EM, and thermal gradients  
- Amplifying captured energy to usable voltages  
- Regulating safely with real-world passive + active systems  
- Operating without fuel, grid, or battery swapouts

> This isn't "infinite energy." It's a well-crafted trap for the energy already present — waiting to be tamed.

---

**Next File:** `/hardware/Field-Harmonic-Control.md`  
→ Controls Tesla harmonic phase tuning and resonance targeting for radiation manipulation

**© 2025 Bryce Wooster — Harvest the Invisible. Charge the Impossible.**
