# Field Tuning & Resonance Module  
**IX-RadiaCore — Harmonic Control Logic for Targeted Radiation Convergence**

This file defines the logic and real-world circuitry that governs how the Tesla coil output is harmonically tuned, phase-aligned, and resonance-adaptive for precision field effects.

---

## 🎯 1. Why Tuning Matters

Tesla-style harmonic fields are not static.  
To draw in airborne radiation and ambient energy effectively, the system must:

- Adapt frequency based on local EM impedance
- Shift phase for maximum dielectric interaction
- Avoid creating harmonic standing waves that destabilize electronics nearby

In short: **If you don’t tune, you can’t hunt.**

---

## 🔧 2. Core Components

| Component | Role | Real Part Examples |
|----------|------|--------------------|
| VCO (Voltage Controlled Oscillator) | Frequency source (10kHz–1MHz sweep) | XR2206, AD9850 (digital) |
| Digital Potentiometer | Adjust oscillator sweep range on the fly | MCP41010 |
| Pulse Width Modulator | Control duty cycle of Tesla pulse train | TL494 or SG3525 |
| Harmonic Filter Array | Remove harmonic distortion/reflections | Custom LC ladder, toroidal chokes |
| Feedback Loop Sense Coil | Detect field load conditions | 30-turn air coil |

---

## 📈 3. Tesla Pulse Configuration

### Default Sweep Range:

- **Frequency**: 14kHz – 80kHz  
- **Duty Cycle**: 50% (nominal)  
- **Phase Drift Correction**: ±3µs dynamic tolerance  
- **Voltage Out**: 30V–1200V peak (step-up range)  
- **Power Draw**: 3W–50W variable (matches environment)

Output is magnetically coupled into a bifilar Tesla coil optimized for low-voltage ambient interactions — not discharge arcing.

---

## 🧬 4. Harmonic Sweep Algorithm

```pseudo
init()
{
  freq = 14kHz;
  while (active)
  {
    measure_EM_field();
    measure_CPS_rate();
    adjust_sweep_window();   // Tune toward maximum ion pair yield
    adjust_pulse_width();    // Prevent field collapse
    if (resonance_peak_detected)
        narrow_band_lock(freq);
  }
}

The algorithm continuously adapts the Tesla pulse based on EM feedback, field stress, and sensor data. Lock-on only occurs when resonance convergence is detected — ensuring minimal stray field bleed.

🌀 5. Adaptive Frequency Lock
Uses real-time signal reflection on the sense coil

If reflected EM power exceeds input, it indicates harmonic resistance

VCO is stepped ±250Hz around target window until null zone found

Resonance "lock" then engaged for up to 5 seconds unless external changes occur

This avoids wasting energy and prevents localized EM overpressure zones.

🛠️ 6. Build Notes
Toroidal chokes should be wound with 22–26 AWG enameled copper

Harmonic filters should cover 3rd, 5th, and 7th harmonics (not just base)

Always shield oscillator stage from coil output — use grounded copper tape

📡 7. Field Effect Shaping
Tesla field interaction is shaped using:

Directional Grounding Plane → One side of the unit has higher EM sink capacity (copper mesh + ferrite)

Reflective Baffle Array → Aluminum shield shapes field flow away from operator or craft

Phase Steered Output → PWM phase offset modulates left/right coil output if needed (for twin coil builds)

✅ Summary
The Tesla core doesn’t just fire — it sings.
It adapts, it harmonizes, it hunts through the static and finds the weak spots in ambient fields where radiation is most unstable.

When the right frequency hits the right spot — the radiation moves.
