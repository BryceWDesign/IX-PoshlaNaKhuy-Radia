# Geiger and Environmental Sensing  
**IX-RadiaCore — Radiation Detection, Field Telemetry, and Environmental Feedback**

This subsystem enables the RadiaCore unit to:
- Detect ambient radiation levels in real time  
- Log intensity and decay rates  
- Reactively tune harmonic field draw based on exposure hotspots  
- Maintain safe operational bounds and power gating based on environment

---

## ☢️ 1. Radiation Detection

### Primary: Geiger-Müller Tube

| Tube Model | Compatible Modules |
|------------|---------------------|
| SBM-20 | DIYGeiger, RH Electronics |
| M4011 | JYE Tech, AliExpress kits |
| SI-29BG | Commercial-grade |  
| J305 (Russian) | High-sensitivity variant |

### Key Metrics Logged:
- Counts Per Second (CPS)  
- μSv/hr (converted via tube-specific calibration factor)  
- Delta-over-time (radiation shift rate)  
- Pulse strength (optional, with preamp)

---

## 🔌 2. Signal Processing

- **Preamp board** buffers and shapes pulses  
- Output connected to:
  - **Interrupt-capable digital pin** on microcontroller (e.g., ESP32, STM32)  
  - **Optional analog comparator** for fine pulse detection  
- Software counter converts to exposure rate with custom calibration table

---

## 🧠 3. Environmental Sensor Suite

| Metric | Sensor | Notes |
|--------|--------|-------|
| Temperature | BME280 or MCP9808 | ±0.25°C accuracy |
| Humidity | SHT31 or DHT22 | 2–5% margin |
| Pressure | BMP388 or MS5611 | For altitude and airflow mapping |
| Gas Composition | MQ-131 (ozone), MQ-135 (general VOC) | Optional |
| EM Disturbance | HMC5883L, QMC5883 | Compass & field tracking |
| RF Noise | Generic SDR (RTL-SDR), or ESP32 RF sweep | Optional, advanced use only |

---

## 📈 4. Data Logging and Control Reaction

Microcontroller:
- Logs data every 1–10s depending on activity  
- Compares against:
  - Threshold trigger levels (e.g., >2.5 μSv/hr = emergency mode)  
  - Change rate slopes (e.g., sudden jump = move/boost field)  
- Sends signals to:
  - Tesla coil tuner for field redirect  
  - Power module to increase draw rate  
  - Alert system (LED, buzzer, or serial packet)

All logs saved to:
- EEPROM (short-term)  
- Optional: SD card (long-term)  
- Optional: Serial/UART output (to drone, dashboard, or GCS)

---

## 🧪 5. Calibration Process

1. Factory default uses baseline curve from sensor datasheet  
2. Optional field calibration using:
   - Known check source (e.g., Uranium glaze, lantern mantle)  
   - Comparison with commercial dosimeter  
3. Software gain multiplier adjusted in EEPROM

---

## 🛠️ 6. Integration and Shielding

- Tube mounted in isolated Faraday-lined chamber  
- Avoid direct line of sight to HV systems (reduce EMI)  
- Use ceramic standoffs or vibration dampers if mobile  
- Cable shielding: braided or foil-wrapped + grounded

---

## ✅ Summary

This module gives the RadiaCore system:
- True autonomous adaptation to real-world radiation  
- Dynamic field control based on threat level  
- Logged analytics for mapping and exposure tracking  
- Full survivability from high-radiation zones with onboard telemetry

> You can’t fight what you can’t see. Now we see it — in every microsecond that counts.

---

**Next File:** `/hardware/Structural-Housing-and-Deployment.md`  
→ Covers material choice, thermal shielding, airflow routing, and modular deployment prep

**© 2025 Bryce Wooster — Read the Fallout. React Without Hesitation.**
