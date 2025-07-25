# Power Input Architecture  
**RadiaCore Energy Ingestion and Load Management Stack**

This file defines how the system:
- Accepts **multiple ambient energy inputs**
- Powers **mission-critical subsystems**
- Regulates, buffers, and isolates **Tesla pulse activity**
- Prioritizes **self-sufficiency first**

---

## ⚡ Power Sources (Supported Inputs)

| Source Name      | Voltage Range | Type              | Priority Tier |
|------------------|---------------|-------------------|----------------|
| ZeroCell Core    | 2.4–3.3V      | Ambient harvester | Tier 1         |
| CryoCore Stack   | 4.2–5.0V      | Thermal delta     | Tier 1         |
| Solar Panel      | 6–12V         | Photovoltaic      | Tier 2         |
| Lithium Battery  | 7.4–11.1V     | Li-Ion, fallback  | Tier 3         |
| External DC Bus  | 9–24V         | Vehicle tether     | Tier 4         |

> All sources are fused and surge-protected at input before entering regulation path.

---

## 🔌 Input Routing Matrix

The system uses a **priority cascade** model:

```plaintext
[ZeroCell] ─┬─┐
[CryoCore] ─┘ │──→ DC-DC Boost 5V (TPS61088)
[Solar] ─────┤
[Battery] ───┤──→ MCU Logic Rail (5V, LDO Regulated)
[External DC]│
             └──→ Pulse Driver Path (Adjustable HV Boost)

🔋 Energy Reservoir
Before being used or pulsed, energy flows into:

Supercapacitor Buffer: 25–50F @ 2.7V

Optional: LiFePO4 Backup Cell (3.2V nominal)

Isolation FETs prevent reverse draw from sensitive sources

Used to:

Absorb spikes from CryoCore/ZeroCell

Deliver short bursts to Tesla driver (~30W peak)

Prevent brownout during pulse/thermal surge

📟 Power Control MCU Logic
Central microcontroller (ESP32 or STM32) monitors and switches sources dynamically:

Voltage Event	Action Taken
ZeroCell/Cryo > 2.5V	Prefer as primary supply
Solar > 6V, battery low	Switch to solar as Tier 2
Battery < 6.5V	Cut pulse activity, telemetry remains
Supercap < 2.1V	Enter recharge-only mode
External DC present	Auto-enable full system performance

🧰 Real Components (Suggested)
Subsystem	Suggested Part	Notes
Boost Regulator	TPS61088, MT3608	Low-voltage to 5V
HV Boost Driver	XL6009 / LT3750	Pulse module voltage source
Supercapacitor	Eaton 50F 2.7V or similar	Energy sponge
Power Switch FET	IRF9540 or P-MOS	Protect low-V sources
Battery Monitor	INA219 or INA3221	Current + voltage telemetry

🧠 System Behavior Summary
Tesla pulses only fire when enough stable power is present

No source is drained to critical unless fallback is confirmed

Field teams can plug in USB-C or 12V at any time to “resurrect” unit

Radiation capture does not require solar or battery input — it runs indefinitely under ambient input in low-CPM zones

🌐 Future-Proof: Smart Grid Ready?
Yes. The architecture:

Supports direct power-sharing over CAN bus or RS485

Can accept drone bus voltage if future flight chassis is added

Easily links to external energy nodes or emergency stations

✅ Summary
Power is not a luxury. It’s the blood supply of every pulse, sweep, and reading this system performs.

Whether airborne, solar-shielded, or crawling through frozen fallout, the IX-PoshlaNaKhuy-Radia system feeds on ambient energy like a predator on instinct — adapting, regulating, and outlasting every dumb battery-only platform.

Next File: /software/Smart-Sweep-Control-Algorithm.md
→ We’ll now code the brain of the sweep pulses: how it detects, adjusts, and adapts pulse frequency + strength to radiation levels dynamically.

© 2025 Bryce Wooster — Power Drawn. Not Borrowed.
