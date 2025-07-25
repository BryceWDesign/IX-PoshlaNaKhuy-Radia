# Deployment Configuration & Mounting Guide  
**IX-RadiaCore — Flexible Platform Mounting and Field Integration**

This file defines how to physically deploy the radiation extraction and neutralization system across multiple mission platforms — from drones to helicopters to backpack rigs. Each mounting config is designed for **real-world terrain**, **power access**, and **safe airflow dynamics**.

---

## 🚁 1. Supported Platforms

| Platform | Mount Type | Notes |
|----------|------------|-------|
| Drone (quad/octo) | Belly Mount (centered CG) | Requires vibration damping |
| Helicopter | Side Pod or Skid Bracket | Use thermal isolation plate |
| Ground Rover | Roof or Rear Cargo Mount | Air intake must face away from exhaust |
| Human-Carried | Backpack Rig | Needs shock isolation and airflow tube redirect |

All versions use the **same internal radiation core**, just different exo-bracket and shock insulation strategies.

---

## ⚖️ 2. Weight and Balance Considerations

**Total Mass (Core Unit):** ~9.8 kg (fully assembled with shielding trays)  
**CG Offset:** All major weight is centered within ±3cm of housing midpoint  
**Wind Drag Profile:** Cylindrical or flattened elliptical housing recommended

**Centering Rules:**
- Must not offset drone CG beyond ±2cm
- Avoid direct EM field alignment with IMU or GPS modules
- Keep intake exposed to airstream — but downstream from propwash

---

## 🧯 3. Vibration Isolation & Shock Mounts

Use **4-point rubber bushing dampers** or **Sorbothane pads** between baseplate and vehicle chassis.

Avoid:
- Metal-to-metal mounting
- Co-locating next to heat-generating systems
- Rigid bolted attachments without suspension points

Recommended materials:  
- Neoprene rubber grommets (10mm)  
- 3D-printed flex-poly brackets  
- Sorbothane washers (40–60 durometer)

---

## 🌬️ 4. Airflow Management

Radiation draw relies on **clean, laminar airflow** through the intake mesh and ion capture bay.

**Guidelines:**
- Always mount intake side forward-facing (or sideways on helicopter with open crosswind)
- Allow minimum **120mm clearance** around intake
- Use baffle shield if high particulate environment is expected

⚠️ Do not place near downwash, exhaust ports, or inlet obstruction zones.

Optional Add-ons:
- HEPA pre-filter snap-on frame  
- Active ionizing ring for turbulent field generation upstream

---

## 🔋 5. Power + Signal Routing

All mounts must provide:
- **18–36V DC input** (step-down converters available)
- **1x Data/Telemetry Line** (CANbus, UART, or i2c supported)
- **1x Power Fail Reset Wire** (fallback capacitor drain logic)

Use shielded JST or XT60 connectors for power, and silicon jacketed 20–22 AWG wires.

---

## 🧳 6. Quick-Release and Maintenance Access

Design should allow:
- Full cartridge access without dismounting entire unit
- Latch-based tray replacement (mesh, zeolite, bioglass)
- Slide-out PSU/fan maintenance from rear

Use spring-pin mounts and captive hardware where possible for **field servicing**.

---

## 🛡️ 7. EM Shielding Notes

Due to onboard Tesla core and pulse driver modules, ensure:
- Adjacent avionics are shielded with grounded foil or Faraday cage net
- Wiring is twisted pair and grounded at single side only
- All metallic surfaces bonded to ground where vehicle spec allows

---

## ✅ Summary

> A radiation predator is only as good as the mount that keeps it airborne, mobile, and unfailing.

This file ensures **anyone** can mount, run, and **trust this device** — whether airborne, crawling, or walking.

---

**Next File:** `/software/Main-Controller-Logic.md`  
→ We’ll code the real-world microcontroller logic that operates sensor polling, Tesla sweep control, resonance lock, power conditioning, and telemetry — in actual pseudocode ready for ESP32, STM32, or RP2040 platforms.

**© 2025 Bryce Wooster — If It Moves, It Can Mount. If It Breathes, It Can Heal.**
