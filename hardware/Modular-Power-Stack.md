# Modular Power Stack  
**IX-RadiaCore — Energy Aggregation, Boost Control, and Tesla Field Routing**

This file defines the full electrical power stack for RadiaCore. The system is modular, hybrid, and self-sustaining when ambient energy is available.

---

## 🔋 1. Core Power Inputs

| Source | Voltage Range | Notes |
|--------|---------------|-------|
| Lithium Battery | 3.7V–12.6V | 3S packs preferred, protected |
| Supercapacitor Stack | 2.5V–15V | Maxwell or LSUC cells (fast discharge buffer) |
| Solar Panel | 6V–20V | 5–40W, flexible mono-crystalline |
| RF Ambient Harvesters | 0.2–3V | Trickles into capacitor over time |
| Tesla Ambient Rectifier | AC/induced | Extracts stray EM bursts for storage |

All inputs flow through **reverse polarity protection** (Schottky diodes or MOSFET gate switches).

---

## ⚡ 2. Central Power Bus

A central high-current DC rail (12V or 18V nominal) feeds all modules.

- **Buck/Boost Converters**:
  - Step-up supercap or lithium to 12V regulated
  - Step-down to 5V and 3.3V for sensors and control logic

- **Power Distribution Board**:
  - Common ground star
  - Ferrite beads on sensitive signal lines
  - Dual shunt resistors for monitoring charge/discharge

- **Auto-switchover** between inputs:
  - Diode-priority or ORing controller
  - Smart switchover logic for power source balancing

---

## 🔁 3. Recharge + Harvest Integration

| Source | Method |
|--------|--------|
| Tesla Coil Capture | AC coupling to bridge rectifier → boost converter → supercap |
| Solar | MPPT controller → lithium charge circuit |
| RF/EM | Harvester → capacitor bank → regulated buffer |
| Vibration (optional) | Piezo → rectifier → charge pump

> Output from Tesla’s field draw loop partially re-routed to capacitor stack after harmonic pulse decay.

---

## 🧠 4. Power Monitoring & Logic

Microcontroller reads:
- Input voltage levels  
- Output load current (INA219 / INA260)  
- Temperature (to throttle if > 70°C)  
- Source selection (priority matrix)

Triggers:
- Cutoff under 3.2V (low batt)  
- Coil pulse damp if overheating  
- LED + audible warning (or remote signal packet)

---

## 🔌 5. Power Output Map

| Module | Voltage | Notes |
|--------|---------|-------|
| Tesla Coil Stack | 12V (isolated) | Boosted internally to HV via flyback |
| MCU + Sensors | 3.3V / 5V | Linear or switch-regulated |
| Geiger & Acoustic | 5V / 12V | Class-D amp isolated from MCU rail |
| Logging + Comms | 3.3V / 5V | UART-safe |
| Fan + Cooling | 12V | Controlled by temp sensor logic |

---

## 📦 6. PCB Notes (if custom built)

- 2oz copper recommended  
- Star grounding  
- Isolated coil and amp rails  
- Fused power paths (PPTC or blade fuse)  
- Test points for debug probes  
- LEDs: Power OK, charging, fault

---

## ✅ Summary

RadiaCore’s power system is:
- Modular  
- Hybrid  
- Self-recharging  
- Protected  
- Field-maintainable  
- Open-loop aware and closed-loop responsive

> Power is not just capacity. It’s timing, tuning, and control. This system obeys that law.

---

**Next File:** `/hardware/Field-Intake-and-Draw-Grid.md`  
→ Defines the physical and electrical logic of the front-facing radiation intake, convergent field shaping, and grid harmonics.

**© 2025 Bryce Wooster — No Power Left Untapped. No Draw Left Unused.**
