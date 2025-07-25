# Geiger + EM Sensor Logic  
**IX-RadiaCore — Real-Time Radiation Detection and Field-Control Feedback**

This document defines how the system senses ambient radiation levels, identifies energy spikes, and dynamically adjusts its behavior based on live telemetry.

---

## 🧠 1. System Function

The sensor array performs five critical functions:

1. Detect background radiation (CPS = counts per second)
2. Sense magnetic flux density around field cores (Tesla choke coil)
3. Detect local EM field instabilities from high ionization regions
4. Adjust harmonic field amplitude + pulse width in real time
5. Trigger emergency shutdown or dampening if safe thresholds are exceeded

---

## 📡 2. Sensor Array Components

| Sensor | Function | Model Example |
|--------|----------|---------------|
| Geiger Tube | Detect ionizing radiation | SBM-20, J305β, SI-29BG |
| Geiger Module | Pulse amplification + UART output | GY-GM V1.0, CJMCU |
| Hall Effect Sensor | Detect EM flux near core | A3144, ACS712 |
| EM Field Sensor | Detect ambient field noise | AD8232 (modded), EMI Sniffer |
| Temp Sensor | Monitor chamber heat | DS18B20 or TMP36 |
| Vibration Sensor | Detect shock/external impact | SW-420 |

All sensors are inexpensive, available on global markets, and Arduino/RPi-compatible.

---

## 🔄 3. Signal Flow Architecture

```plaintext
[Geiger Pulse] ──► MCU INT Pin ─► Pulse Timer  
[Hall Sensor] ──► ADC Read ─► Field Strength Evaluation  
[EM Sensor] ──► FFT Analysis ─► Noise & Spike Detection  
[Temp Sensor] ──► Safe Operating Limits  

🧬 4. Field Feedback Logic
A. Adaptive Tesla Harmonic Loop
Condition	Detected	Action
Radiation ↑	CPS > Threshold	Increase Tesla loop pulse width
EM Instability	FFT spike pattern	Dampen harmonic resonance slightly
Temp ↑↑	> 60°C	Throttle Tesla loop, lower frequency
External Spike	Sudden CPS jump	Trigger brief pulse shutoff, 2s reset

🛑 5. Emergency Safeguards
Radiation > CPS Max Threshold (e.g., 300 CPS sustained for 10s)

Auto-disable Tesla output

Vent chamber fan to increase dilution

Flash red LED + audio beep for 5s

Log event to onboard SD or serial

Power Drain Fault

If draw exceeds buffer by 30%

System resets field loop to minimum

EM Feedback Loop Saturation

If harmonic reflections spike → fallback to idle sweep

🧠 6. Intelligence Loop (Basic Code Logic)
if (CPS > 100 && CPS < 200) {
   pulseWidth = 80;
   frequency = 18kHz;
}
else if (CPS >= 200 && CPS <= 300) {
   pulseWidth = 100;
   frequency = 21kHz;
}
else if (CPS > 300) {
   disableTesla();
   alert();
}

Pulse widths are tied to resonance response curve — tuned during calibration stage.

🧪 7. Calibration Method (Field Tuning)
Place unit near known weak radioactive source (e.g., thorium lantern mantle or test check source)

Observe CPS output curve vs Tesla amplitude

Adjust field loop PWM range for resonance match

Repeat under different temperatures to validate thermal drift resilience

✅ Summary
The sensor logic:

Detects what the eye cannot see

Controls energy like a valve, not a trigger

Ensures safety, stability, and intelligent field behavior in every mode

Without feedback, it’s just a blind machine. With this logic — it sees, it adapts, it survives.

Next File: /hardware/Power-Buffer-and-Scavenging.md
→ Now we define how this predator feeds: what it eats, how it digests radiation into energy, and how it stores what it doesn't use.

© 2025 Bryce Wooster — Let the System Think for Itself.

