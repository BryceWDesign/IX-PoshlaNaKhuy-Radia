# Main Controller Logic — RadiaCore System  
**Target Microcontrollers:** ESP32, STM32, RP2040 (or equivalent with ≥ 2 cores and ADC/DAC support)

This file defines the core embedded logic governing the behavior of the IX-PoshlaNaKhuy-Radia system:
- Radiation detection and analytics
- Ambient power draw and distribution
- Tesla resonance sweep coordination
- Discharge gate triggering and thermal management
- Telemetry and watchdog control

---

## 🧠 Core Architecture

```plaintext
┌────────────────────────┐
│ SENSOR POLLING LOOP    │
│ - Radiation sensor     │
│ - Ambient voltage      │
│ - Thermal feedback     │
└────────────┬───────────┘
             ↓
┌────────────────────────┐
│ RESONANCE CONTROL UNIT │
│ - Harmonic sweep       │
│ - Tesla pulse logic    │
│ - Phase feedback       │
└────────────┬───────────┘
             ↓
┌────────────────────────┐
│ POWER MGMT + BUFFERING │
│ - Cap bank monitoring  │
│ - Auto switch source   │
└────────────┬───────────┘
             ↓
┌────────────────────────┐
│ DISCHARGE COORDINATOR  │
│ - Pulse to mesh window │
│ - Venting & shielding  │
└────────────┬───────────┘
             ↓
┌────────────────────────┐
│ TELEMETRY + WATCHDOG   │
│ - Serial/CAN/i2c out   │
│ - Failover handling    │
└────────────────────────┘

🔁 Main Loop Logic (Pseudocode)

loop() {
  pollSensors();                      // radiation, temp, voltage
  updateResonanceSweep();            // maintain harmonic lock
  managePowerFlow();                 // ambient energy OR battery
  handleDischargeWindow();           // fire pulse if threshold met
  broadcastTelemetry();              // optional serial/i2c
  watchdogCheck();                   // reboot if anomalous
  delay(10);                         // maintain 100 Hz loop
}

🔬 Key Subsystems (Real-World Components)
1. Radiation Sensor Input
Compatible: RadSens v3, SBM-20, SiPM counters

Connected via analog or pulse input

Trigger threshold set in EEPROM or hardcoded

2. Tesla Pulse Sweep Logic
Driven by PWM on high-voltage driver

Frequency range: 18–55 kHz sweep + harmonics

Bifilar coil tuned dynamically based on feedback

3. Ambient Energy Capture Interface
Reads voltage from ZeroCell, CryoCore, or solar/battery hybrid

Swaps to backup cap bank if low

4. High-Energy Discharge Control
GPIO toggles solid-state relay (SSR) or opto-isolated gate

Activates plasma mesh window (timed ~50–200 ms bursts)

Ensures cooldown between pulses

5. Telemetry (Optional)
CANbus (preferred), or Serial UART

Transmits:

Radiation count

Internal temp

Voltage in/out

Pulse rate

Status flags

⚙️ Recommended Libraries (for Arduino / PlatformIO)
- Adafruit_Sensor
- OneWire / DallasTemp
- Preferences (EEPROM)
- AsyncCAN / CANopen
- WiFiManager (if ESP32 WiFi telemetry used)

💥 Fail-Safe Behavior
If radiation spikes but discharge fails → shut down and retry after cooldown

If voltage drops below 5V → switch to alternate input or disable Tesla pulse

If coil temp > 65°C → pause harmonic sweep

If watchdog not reset within 2s → full system reboot

✅ Summary
This is the brain that thinks like a field engineer, reacts like a medic, and pulses like Tesla himself had a vendetta against gamma rays.

This file brings all hardware to life — sensors, energy systems, pulses, and safety logic in one tight loop.

Next File: /software/Telemetry-and-Diagnostics.md
→ We’ll build the external interface: how to monitor this system in the field (laptop, tablet, drone uplink, etc.) using safe, encrypted comms, with diagnostics for field engineers.

© 2025 Bryce Wooster — When the Pulse Hits, Radiation Doesn’t Get Up.
