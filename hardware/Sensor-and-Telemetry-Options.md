# Sensor and Telemetry Options  
**IX-RadiaCore — Modular Diagnostics, Radiation Sensing, and Data Transmission**

This document outlines the **sensor arrays** and **telemetry systems** that can be integrated into IX-RadiaCore for real-time diagnostics, environmental logging, radiation monitoring, and remote status alerts.

---

## 🎯 1. Core Objectives of Telemetry

- Monitor environmental conditions (radiation level, humidity, pressure)  
- Track internal health (temperature, power draw, airflow, coil frequency)  
- Enable live or logged data review (SD, wireless, or satellite)  
- Power-efficient and modular with COTS components only

---

## 📡 2. Sensor Categories

### A. Radiation Sensors
| Sensor | Type | Detects | Notes |
|--------|------|---------|-------|
| SBM-20 | Geiger–Müller tube | Beta, Gamma | Low-cost, widely available |
| SI-8B | Geiger tube | Gamma | High sensitivity |
| PIN Photodiode + OpAmp | Solid-state | Alpha/Beta | Needs calibration shielding |
| Neutron Bubble Dosimeter | Passive | Neutron | One-time use (optional backup only) |

---

### B. Environmental Sensors
| Sensor | Measures | Model |
|--------|----------|-------|
| BME688 | Temp, humidity, pressure, gas detection | I2C |
| MQ-131 | Ozone | High sensitivity, analog |
| DHT22 | Humidity + Temp | Low-cost alternative |

---

### C. Internal Health Monitoring
| Sensor | Measures | Location |
|--------|----------|----------|
| INA219 | Voltage + Current | Power loop monitor |
| DS18B20 | Temperature | Near Tesla coil + power caps |
| Flow Sensor (Honeywell AWM720P1) | Air draw rate | Behind HEPA intake |
| Accelerometer (MPU6050) | Vibration + impact | Mounted center chassis |

---

## 🧠 3. Sensor Hub Architecture

- MCU: ESP32, STM32, or RP2040 preferred  
- Power: 3.3V / 5V regulated via onboard buck converter  
- Comm protocols: I2C, UART, SPI (multiplexed if needed)  
- Optional: External ADC for high-accuracy analog readings  
- Logging: 16GB+ SD via SPI or I2C real-time clock chip

> 🔐 All sensor data is **non-identifiable**, offline-compatible, and does **not require internet** access.

---

## 📶 4. Telemetry Options

| Method | Range | Notes |
|--------|-------|-------|
| LoRa 915 MHz | 2–10 km LOS | Ideal for remote/rural ops |
| WiFi ESP-NOW | 30–100m | Low-power, mesh-capable |
| Bluetooth LE | ~10m | Short-range diagnostics |
| Serial to SDR | Unlimited | For use with HAM/Sat uplinks |
| SD Logging | Offline | Always-on fallback |

> 🛰️ Optional: Iridium RockBLOCK 9603 or Swarm satellite modem for ultra-remote ops (if permitted by law)

---

## 🔋 5. Power Efficiency

- Average draw: ~35–100 mA depending on sensor combo  
- Sleep mode possible on MCU with wake-on-event  
- Telemetry duty-cycled at intervals (configurable 1s–10min)  
- LoRa can send <200 byte packets with <50mW burst

---

## 🔧 6. Data Format

Default: JSON or CSV over serial/LoRa

```json
{
  "radiation_uSv": 16.3,
  "temp_C": 42.1,
  "airflow_lpm": 23.4,
  "cap_voltage": 11.92,
  "coil_freq_Hz": 512300,
  "battery_percent": 89,
  "timestamp": "2025-07-24T13:26:00Z"
}

## 📂 7. Modular Config Guidelines
Minimum viable: 1x Geiger, 1x Temp, 1x Current Monitor

Full config: All arrays + SD logger + LoRa module

All sensors hot-swappable via JST-GH or Molex MicroFit headers

Weatherproofed ports via rubber caps or epoxy strain relief

✅ Summary
Real-time feedback enables:

Safer field operations

Performance tuning

Auto-shutdown thresholds

Proof-of-function during deployment

All sensor packages are:

COTS

Open source-supported

Globally available

100% legal, no export restrictions

Next File: /hardware/EM-Surge-Protection-and-Hardening.md
→ Includes real-world suppression, clamping, and failover for EMP/high field ops

© 2025 Bryce Wooster — If You Can’t Measure It, You Can’t Save It
