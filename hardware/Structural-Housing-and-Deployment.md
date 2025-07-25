# Structural Housing and Deployment  
**IX-RadiaCore — Ruggedized Housing, Radiation Shielding, and Modular Attachment Strategy**

This file outlines the structural, environmental, and field-ready considerations for physical deployment of the IX-RadiaCore unit.

---

## 🧱 1. Enclosure Material Options

| Layer | Material | Purpose |
|-------|----------|---------|
| Outer Shell | ABS or Polycarbonate | Impact resistance, UV/weather durability |
| Inner Chassis | 6061 Aluminum or Titanium | Structural rigidity, grounding frame |
| EM Shield Layer | Copper mesh / foil | EMI/RFI shielding |
| Radiation Barrier | Boron-infused HDPE or Leaded Acrylic | Attenuates scattered radiation from draw |
| Thermal Wrap | Aerogel sheets + Mylar | Heat isolation, fire resistance |

---

## ❄️ 2. Thermal Regulation

### Passive Cooling:
- Dual vent channeling w/ mesh filters (upward exhaust, downward intake)  
- Heat sink mounts on:
  - Tesla coil drive stack  
  - Boost module  
  - MCU/sensor zone  
- Optionally add phase-change material near high-draw areas for burst load management

### Optional Active:
- 5V or 12V brushless fans (PWM-controlled via temp sensors)  
- Integrated with radiation sensor logic (boost fan only during high-load event)

---

## 🧲 3. Mounting and Attachment Points

To accommodate both drone and ground use:

### Standard Mount Points:
- 4x M4 threaded brass inserts (side frame)  
- Rail-compatible groove slots (fits DJI or custom sleds)  
- Rear panel anchor tabs (parachute/hardpoint harness)  
- Removable bottom plate (for drone belly or payload drop)

---

## 🔄 4. Deployment Configuration

| Mode | Use Case | Notes |
|------|----------|-------|
| Drone (underslung) | Fly-through sampling, fast sweep | Needs vibration dampers |
| Tripod-mount (static) | Ground scan / long-duration | Add solar panel for passive recharge |
| Backpack-carry | Human deployable | Heatsinks moved to exterior frame |
| Tethered-mast | Elevated operation in wind | Good for air column capture |

---

## 📏 5. Dimensions & Weight Target

| Dimension | Value |
|-----------|-------|
| Width | ≤ 25cm |
| Height | ≤ 18cm |
| Depth | ≤ 15cm |
| Weight (dry) | ≤ 3.5kg |
| Weight (with battery) | ~4.0kg |

**Note**: Modular shielding may add weight based on severity of zone.

---

## 🧩 6. Maintenance and Field Repair

| Component | Access | Tool Needed |
|-----------|--------|-------------|
| Filters | Slide-in hatch | None |
| HV module | Screwed panel | Phillips #1 |
| Tesla coil | Removable shroud | Hex 2.5mm |
| MCU/Telemetry | Rear board tray | Snap release or velcro |
| Battery/supercap | Hinged lid | Quick latch |

> Field deployment assumes **low-infrastructure** environments — design is maintainable by one person, even in protective gear.

---

## ✅ Summary

The IX-RadiaCore is structurally designed to be:
- **Field-viable** — rugged, self-protecting, and weatherproof  
- **Modular** — attachable to drones, tripods, backpacks, or static towers  
- **Shielded** — with proper radiation attenuation + thermal insulation  
- **Repairable** — using simple tools in hostile terrain

> It doesn’t matter how powerful your system is if it can’t survive the field. This one does.

---

**Next File:** `/hardware/Acoustic-Harmonic-Disruption.md`  
→ Introduces directional audio/pressure wave logic to assist particle destabilization and resonance targeting

**© 2025 Bryce Wooster — Built for Where No One Else Dares to Walk.**
