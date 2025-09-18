# Bill of Materials (reference design)

## Air Path & Filtration
- **Pre-filter (G4/MERV 7–8)**: 1× panel, protects downstream stages
- **ESP module (compact, enclosed)**: 1×, 10–15 kV @ µA–mA, rated for continuous air cleaning
  - Requirements: enclosed HV, integrated corona/collection plates or plate bays, remote enable, fault output
- **HEPA H13 cartridge**: 1× mini-pleat panel, ≥99.95% @ 0.3 µm (EN1822 / or 99.97% per US HEPA)
- **Activated carbon bed (KI/TEDA impregnated)**: canister or panel sized for residence time at Q
  - Note: use KI+TEDA or equivalent media validated for radioiodine species

## Fans / Blowers
- **Centrifugal blower** (or dual in parallel) sized for target Q with ΔP 250–350 Pa 
  - 12 or 24 VDC, PWM control; include backdraft damper

## Sensors
- **Geiger–Müller tube** (choose one):
  - **SBM-20** (beta/gamma, cylindrical) + HV driver + pulse conditioning
  - **LND-712** (end-window α/β/γ) for higher sensitivity to β/α near inlet
- **Differential pressure sensor**: ±500 Pa, I²C (estimate Q via calibrated ΔP)
- **Air temp/RH**: for air density correction
- **(Optional)** Hot-wire anemometer for direct Q

## Control & Power
- **MCU**: ESP32 DevKit (Wi-Fi, UART)
- **DC/DC**: 24→12 V (if needed), 12→5 V; isolated supply for ESP HV control lines
- **Connectors, fusing, interlock switches**, enclosure gaskets, EMI shielding

## Mechanical
- **Sealed ducting** between stages; quick-release latches for filter cartridge
- **Service port** (bag-in/bag-out) for HEPA/carbon change
- **Mount kit** for vehicle/duct interface (optional UAV mount requires separate design)

> Notes & references:  
> - HEPA H13 performance per EN1822 / US HEPA specs.  
> - KI/TEDA-impregnated carbons are widely used for radioiodine in nuclear ventilation.  
> - GM tube selection (SBM-20, LND-712) are standard, documented detectors. 
