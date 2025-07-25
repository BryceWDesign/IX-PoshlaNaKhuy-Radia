# IX-RadiaCore — Build Instructions  
**Version 1.0 — July 2025**  
**Author:** Bryce Wooster

This document provides a full, detailed, step-by-step process for physically constructing the **IX-RadiaCore** modular radiation extraction system using real-world components from the included BOM.

All tools, materials, and fabrication methods are accessible to any serious builder with intermediate electronics experience.

---

## 📐 SECTION 1: Fabricate the Chassis

### Materials
- ABS sheet or aluminum plate
- Vent mesh or acrylic side panels
- 3D printed or CNC-cut bracket mounts

### Steps
1. Cut outer case to ~38cm × 38cm × 18cm.
2. Mount **vent mesh** or grille openings on front, back, and lower sides.
3. Attach **mounting rail system** or universal bracket to base.
4. Line interior with **EMI copper mesh or Mu-metal foil** for shielding.

---

## ⚡ SECTION 2: Assemble the Ion Draw Array (IDA)

### Materials
- Stainless mesh panels
- High voltage supply
- PTFE insulators
- Regulator module

### Steps
1. Mount mesh panels in parallel inside intake path (≈2–3 cm gap).
2. Use PTFE insulators to suspend HV mesh safely from grounded chassis.
3. Connect high voltage positive to one mesh panel; ground the other.
4. Integrate voltage regulator and adjust for 20–40kV output.
5. Verify corona onset visually in dark with proper PPE.

---

## 🌀 SECTION 3: Build the Radiation Sink Conduit (RSC)

### Materials
- Bifilar copper coil
- Ferrite core or toroid
- Tesla pulse driver (Arduino/STM32 + driver circuit)

### Steps
1. Wind bifilar coil (16–18 AWG, 20–40 turns) on toroidal ferrite core.
2. Solder leads to pulse driver circuit.
3. Program microcontroller to emit 3-phase Tesla harmonics at 3–6–9 resonance steps.
4. Mount coil inline behind IDA, aligned with airflow direction.
5. Power from APL (12VDC or as needed).

---

## 🔋 SECTION 4: Install Ambient Power Loop (APL)

### Materials
- GaInSn cell core
- Supercapacitors
- Charge balancer
- Boost/buck converter

### Steps
1. Mount GaInSn ZeroCell in thermal isolation chamber near mesh grid.
2. Wire liquid metal cell to capacitor array with charge balancer inline.
3. Connect capacitor output to adjustable DC converter.
4. Route 12–48VDC output to power main system modules.

---

## 🎛️ SECTION 5: Configure Acoustic/EM Disruptor (EAD)

### Materials
- Ultrasonic or magnetostrictive driver
- Tesla sweep modulator
- Pulse timer (555 or MCU)

### Steps
1. Attach acoustic driver behind mesh flow zone (angled or center).
2. Connect pulse timer to modulator and sweep driver.
3. Program for 10μs–100μs bursts across 10kHz–80kHz
4. Ensure audio emissions do not exceed 130dB — buffer with foam.

---

## 🧼 SECTION 6: Build Filter Containment Stack (FCS)

### Layers (from intake to exhaust):
1. HEPA pre-filter
2. Zeolite mineral trap
3. Boron-carbon mesh
4. Acoustic foam baffle

### Steps
1. Construct cylindrical or rectangular filter cartridge body.
2. Insert each layer tightly in stack, allow replaceability.
3. Connect filter housing inline after discharge zone.
4. Optional: install particle counter for saturation tracking.

---

## 🔌 Final Wiring & Power Check

1. Route all module power feeds through the APL ultracap bus.
2. Ensure HV lines are isolated from control systems.
3. Test each module in isolation before full activation.
4. Seal and shield housing, leaving access for filter removal and tuning.

---

## 🧪 Testing + Commissioning

1. Use simulated ionized particle source (safe lab demo powder or ion generator).
2. Observe ion draw and field shaping (use EMF probe, particle counter).
3. Measure power capture curve from APL.
4. Validate filter capture via Geiger counter, if applicable.

---

## Notes

- All wiring should use shielded cables.
- Use grounded anti-static work surface.
- Wear PPE during HV and RF testing.
- Replace filters regularly (24–72 hr use).
- Recommended ambient radiation level: 1–100 μSv/h for optimal scavenging efficiency.

---

This device does **not** eliminate ground-based isotopes or deep soil contamination directly — for that, future modules may be designed.

---

**Next File:** `/docs/Functional-Theory-and-Field-Mechanisms.md`  
→ Will explain why this works, based on real-world science

**© 2025 Bryce Wooster — Licensed for Humanity, Not War**
