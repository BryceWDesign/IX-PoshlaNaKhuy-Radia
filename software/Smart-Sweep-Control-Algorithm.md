# Smart Sweep Control Algorithm  
**Adaptive Pulse Modulation Based on Environment and Power Health**

This algorithm governs how and when the Tesla harmonic discharge system fires during operation — dynamically adjusting for:

- Radiation density (CPM)
- Pulse discharge history
- Ambient energy reserves
- Thermal system status

---

## 🧠 Core Behavior Overview

> Sweep pulses are *not* constant. They adapt.

```plaintext
HIGH RADIATION → FASTER SWEEP RATE
LOW ENERGY     → REDUCED PULSE INTENSITY
HIGH TEMP      → SHORTENED DUTY CYCLE
🔁 Pulse Logic Loop (Every 1000ms)
def update_sweep_logic():
    cpm = read_radiation_sensor()
    v_buffer = read_supercap_voltage()
    temp_core = read_internal_temp()

    # Set base sweep freq
    if cpm > 1800:
        sweep_freq = 62.0  # Hz
    elif cpm > 1000:
        sweep_freq = 48.0
    elif cpm > 500:
        sweep_freq = 33.0
    else:
        sweep_freq = 18.0

    # Modulate power output if buffer is weak
    if v_buffer < 2.4:
        sweep_power = "LOW"
    elif v_buffer < 2.7:
        sweep_power = "MID"
    else:
        sweep_power = "HIGH"

    # Thermally protect system
    if temp_core > 60:
        sweep_freq *= 0.6
        sweep_power = "LOW"

    # Output decision
    set_pulse_parameters(freq=sweep_freq, power=sweep_power)

⚙️ Real Functions (Stub Overview)
Function Name	Description
read_radiation_sensor()	Returns CPM or μSv/h from SiPM/Geiger
read_supercap_voltage()	Reads voltage across energy buffer
read_internal_temp()	Reads onboard thermistor (°C)
set_pulse_parameters(freq, power)	Sends config to Tesla driver

🧪 Example: Field Behavior Simulation
CPM	Voltage	Temp (°C)	Freq (Hz)	Power Level
2200	2.9V	42.1	62.0	HIGH
1200	2.5V	59.8	48.0	MID
700	2.3V	52.3	33.0	LOW
330	2.1V	61.0	10.8	LOW (reduced)

🎛️ User Override Modes
If the user holds the mode switch > 4s, they unlock:
[SAFE MODE]     → Sweep disabled, monitor only
[MANUAL BOOST]  → 30-sec max-power burst (then cooldown)
[INTERMITTENT]  → 5s ON / 15s OFF sweep pattern

These allow:

Conservative burn-in tests

Cold zone mapping with minimal power

On-demand aggressive pulse field

📡 Telemetry Output Hooks
The algorithm updates the main /telemetry output JSON as:
"sweep_freq": 33.0,
"sweep_power": "MID",
"sweep_mode": "AUTO"

🔐 Safety & Resilience
Failsafe triggers include:

CPM drops to 0 for >60s → enters low-duty hibernation

Thermal spike >70°C → sweep disabled for 5 minutes

Watchdog reset → enters SAFE MODE and logs reboot reason

✅ Summary
This is not just a dumb pulse cannon.
It’s a thinking, self-modulating bioelectrical weapon against ambient radiation.
It adapts like a nervous system. It learns by input.
And when needed — it strikes hard, fast, and efficiently.

Next File: /integration/Drone-Mounting-and-Adaptation.md
→ Let’s document the physical integration points, payload clamps, and modular power/data harness to mount this system to any drone, aircraft, or rover platform.

© 2025 Bryce Wooster — Build Smarter, Pulse Harder
