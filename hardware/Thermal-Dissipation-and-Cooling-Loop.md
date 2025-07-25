# Thermal Dissipation & Cooling Loop  
**Heat Regulation for Tesla Pulse Core + Radiation Discharge Hardware**

When dealing with:
- HV plasma discharge
- Ionized radiation fields
- Constant ambient intake
- Bifilar sweep currents

...you get **a heat problem**.

This file defines a **real-world hybrid cooling system** that:
- Requires no exotic materials
- Is buildable with open-source-grade parts
- Can handle long-term drone, mobile, or fixed deployment

---

## 🔥 Heat Sources

| Component           | Thermal Load (Typical) |
|--------------------|------------------------|
| Pulse Cap Bank     | 3–8W during bursts      |
| Plasma Ion Plate   | 10–15W continuous       |
| Tesla Coil Driver  | 2–4W pulse-related      |
| Controller MCU     | 0.5–1.2W                |

---

## 🌬️ Passive Cooling Architecture

**Used when airflow is available (flight, mount, wind):**

- **Aluminum fins** on ion plate and pulse cap bank  
- Open-vent chassis with **side slotted ducts**  
- Black anodized mesh frame coating for IR shedding  
- Thermal pads (1.5–2 W/m·K) between driver and base plate  
- Copper heat pipes optional for horizontal or drone-fitted installs

---

## 💧 Active Cooling (Compact Radiant Loop)

**Used for high-radiation zones or fixed-location deployment**

- **Liquid loop** with 3–5 mm internal tubing  
- **Pump:** 5V DC micro impeller pump (200–300 mL/min)  
- **Fluid:** 80% distilled water + 20% Propylene Glycol (non-toxic)  
- **Reservoir:** 40–60 mL mini fill tank  
- **Cooling block:** Flat copper baseplate under ion trap  
- **Fan + radiator:** 60mm fan over 40x80mm radiator

Total weight: ~120g  
Power draw: ~0.4–0.7W (self-regulating via onboard MOSFET)

---

## 🧠 Smart Cooling Logic (Controlled by MCU)

Temperature sensor (NTC or I2C):
- > 48°C → Enable fan  
- > 55°C → Enable pump  
- > 65°C → Throttle Tesla pulses & log thermal warning  
- < 40°C → Idle pump  
- < 35°C → Disable fan

Fan PWM = directly tied to radiation intensity if telemetry mode is enabled.

---

## 📦 Materials List

| Component        | Suggested Model                     | Notes                             |
|------------------|-------------------------------------|-----------------------------------|
| Copper Baseplate | 40mm x 40mm x 2mm                   | Under ion window                  |
| DC Pump          | PC 5V micro submersible (e.g. JT-180)| Draws <150mA                     |
| Tubing           | Silicone, 4–5mm ID                  | Loop to radiator                  |
| Radiator         | 40mm x 80mm finned aluminum         | Compact, fits drone chassis       |
| Thermal Pads     | 2.0 W/m·K, 1.5mm thick               | For cap bank + driver             |
| Temp Sensor      | NTC 10k or TMP36 / DS18B20          | MCU-connected                     |

---

## 🛑 Safety and Recovery Protocols

- All fluid paths sealed with silicone clamp and epoxy-secured joints  
- Reservoir includes vent check valve for pressure regulation  
- In event of fan/pump failure:
  - Tesla coil auto-throttles
  - Pulse gate discharges to ground
  - Red LED + audible piezo alert tone emitted

---

## 🧪 Deployment Tips

| Situation              | Cooling Mode       | Notes                                      |
|------------------------|--------------------|--------------------------------------------|
| Drone in motion        | Passive only       | Flight air sufficient                      |
| Ground robot or tripod | Passive + fan      | If shielded, add forced air                |
| Fixed radiation zone   | Full loop active   | 24/7 operation mode                        |
| Arctic deployment      | Glycol mix > 30%   | Avoid freeze hazard in loop                |

---

## ✅ Summary

> This is the pulse core’s **internal circulatory system** — invisible to the outside world, but absolutely vital to survival.

It doesn’t overengineer. It doesn’t use fantasy materials. It **cools like a soldier** and stays cold under pressure — so the rest of the system can keep doing damage to what doesn’t belong in the air.

---

**Next File:** `/integration/Power-Input-Architecture.md`  
→ This file defines how all your ambient energy systems (ZeroCell, CryoCore, etc.) plug into this beast — and how the system dynamically draws from and regulates that power.

**© 2025 Bryce Wooster — We Made the Air Bite Back.**
