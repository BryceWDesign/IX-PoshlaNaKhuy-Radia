# Bench & Field Test Protocol

## Purpose
Show that the device (a) captures aerosols that carry radioactivity and (b) logs dose-rate and airflow accurately. 
**We do not claim removal of gamma/neutrons from air.**

## Instruments
- Calibrated **dosimeter** (µSv/h) placed at fixed positions
- **GM CPS** from on-board tube
- **Differential pressure** (ΔP) across HEPA/carbon
- (Optional) Portable particle counter for non-radioactive aerosol tests

## Tests

### A) Functional air test (non-radioactive)
1. Install new prefilter, HEPA, carbon. 
2. Generate an aerosol (NaCl fogger or incense) upstream of inlet in a closed room (~50–100 m³).
3. Run device at each fan duty (25/50/75/100%). Record Q_est (from ΔP), ΔP, and downstream particle counts if available.
**Expected:** Downstream particle counts ≪ upstream; ΔP stable; Q_est within spec.

### B) Dose logging sanity check (background)
1. Place device in a low-background area, fans **off** and **on**. Log CPS and µSv/h for 30 min each.
2. Verify CPS distribution is Poisson-like; fan electrical noise does not produce false counts.

### C) Source-proximate capture (controlled/authorized environment)
1. In a controlled setting with proper authorization and safety oversight, position inlet near a known low-level radioactive aerosol stream (or a surrogate tracer in a lab chamber). 
2. Run at nominal Q. Place reference dosimeters at fixed geometry upstream/downstream.
3. After run, bag-out filters and scan with dosimeter in shielded area.
**Expected:** Dose rate at downstream monitor does not increase; collected media shows elevated counts vs background (if radioactive aerosol was present).

### Data to publish
- Time series: CPS, µSv/h, ΔP, Q_est, fan duty, T/RH
- Photos of setup, dot-plots (CPS vs time)
- If available: gamma spectroscopy of filter media (nuclide ID)

## Acceptance criteria (MVP)
- Particle removal: ≥90% downstream reduction for 0.3–1 µm surrogate aerosol at Q
- Logging: stable CPS with fans on (no EMI artifacts)
- Safety: zero HV trips during continuous 1-hour operation; enclosure temp < 45 °C

## Notes
- If activity is only in gases (e.g., iodine forms), expect minimal response unless carbon is sized and impregnated for those species. 
