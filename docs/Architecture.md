# IX-PoshlaNaKhuy-Radia — Architecture (Capturable Scope)

**Problem:** Remove **radioactive particulate/aerosols** from air streams close to source while logging dose rate and airflow.  
**Non-goals:** Removing gamma/neutrons from open air (requires shielding, not feasible for portable device).

## Air Path (sealed)
[Inlet] → Pre-filter (G4) → **ESP stage** (pre-charge + collector plates) → **HEPA H13** → **KI/TEDA-impregnated activated carbon** → [Outlet]

## Performance Targets
- Nominal flow **Q = 0.05–0.2 m³/s** (≈100–400 CFM) depending on build.
- ESP single-stage efficiency target **η_ESP ≥ 0.7** at design Q.
- Overall particulate removal (ESP + HEPA) ≥ **99%** at 0.3–1 µm.
- Pressure drop across HEPA + carbon ≤ **350 Pa** at Q (pick fan accordingly).

## ESP Sizing (Deutsch–Anderson)
\[
\eta = 1 - \exp\!\left(-\frac{A\,w}{Q}\right)
\]
With **w ≈ 0.03–0.06 m/s** (typical migration velocity range), **Q = 0.05 m³/s**, **η = 0.7** →  
Required plate area **A ≈ 1.0–1.7 m²** (stacked plates / honeycomb). Increase A or reduce Q to raise η.  
**Note:** Use published w or measure; do not assume ideal. 

## Power Budget (example @ Q≈0.05 m³/s)
- Blower (ΔP≈250–300 Pa) ………………… 12–30 W  
- ESP HV module (10–15 kV, µA–mA) ……  5–20 W  
- MCU + comms + sensors ………………… 1–3 W  
**Total:** ~18–53 W (battery or 12–24 V vehicle bus)

## Electronics
- **MCU:** ESP32 (UART/Wi-Fi)  
- **Dose sensor:** GM tube (SBM-20 or LND-712 w/ driver), or compact NaI(Tl) if budget allows  
- **Airflow:** pitot + differential pressure (e.g., ±500 Pa) and/or in-duct anemometer  
- **Power:** 12–24 V input → DC/DC rails + isolated HV for ESP

## Data
- Logs: timestamp, GPS (if mobile), µSv/h, counts per second (CPS), ΔP, Q_est, fan duty.  
- Interfaces: UART, Wi-Fi, optional I²C for autopilot.

## Safety & Compliance
- HV interlocks; insulated ESP compartment with bleeder resistors.  
- Filter cartridge change-out in sealed bags (see Safety.md).  
- Follow local rules for handling **potentially contaminated HEPA/carbon**.
