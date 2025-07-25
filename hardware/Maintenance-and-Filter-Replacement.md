# Maintenance and Filter Replacement  
**IX-RadiaCore — Safe Filter Handling, Replacement, and Long-Term Maintenance**

This document provides detailed procedures for:
- Replacing contaminated filters  
- Handling radiation-laden components  
- Performing preventative maintenance on system subsystems  
- Ensuring longevity and safety in the field

---

## 🧼 1. Filter System Overview

The **Filter Containment Stack (FCS)** includes 4 layers:

| Layer | Function |
|-------|----------|
| 1. HEPA Nanofiber | Captures microdust, aerosol-bonded isotopes |
| 2. Zeolite | Absorbs Cesium-137, Strontium-90 |
| 3. Boron-Carbon Mesh | Neutron moderation, additional binding |
| 4. Acoustic Baffle | Dampens harmonic pressure + traps floating fines |

---

## ⏱️ 2. Replacement Timeline

| Radiation Zone Level | Recommended Filter Replacement Interval |
|----------------------|------------------------------------------|
| Low (1–10 μSv/h)     | 72–96 hours |
| Medium (10–50 μSv/h) | 48–72 hours |
| High (>50 μSv/h)     | 24–48 hours |

Replace filters sooner if:
- Ion draw efficiency drops by >30%  
- Visual inspection shows buildup  
- Exhaust airflow is restricted

---

## 🧰 3. Tools Required

- Anti-static gloves  
- Radiation-rated mask (N95+ minimum, P100 ideal)  
- Radiation-safe waste bag or container  
- Wipe-down cloths (isopropyl alcohol)  
- Clean replacement filter cartridge  
- Optional: Geiger or alpha-beta particle counter

---

## 🚿 4. Removal Procedure

1. Power down and discharge all subsystems (use Field Checklist)  
2. Unscrew or unclip the lower filter housing  
3. Slide out cartridge gently — **do not shake or invert**  
4. Place directly into sealed waste bag or lead container  
5. Wipe down cavity with alcohol + cloth  
6. Insert new clean cartridge; reseal housing

> ⚠️ If cartridge appears wet, swollen, or ruptured — treat as high-risk waste

---

## ♻️ 5. Disposal Protocol

- Seal used filters in **thick HDPE bags or shielded containers**  
- Label clearly as **contaminated radioactive waste (low-level)**  
- Store away from humans, animals, or food areas  
- Follow local radiation disposal guidelines  
- NEVER incinerate or crush contaminated filters

---

## 🔧 6. Subsystem Maintenance (Weekly or per 5 deployments)

| Subsystem | Task |
|-----------|------|
| HV Mesh   | Inspect for corrosion, clean with isopropyl if needed |
| Tesla Coil | Re-tune driver, verify resonance with scope |
| ZeroCell | Check for oxide buildup, purge if >30% surface change |
| Capacitor Bank | Confirm no swelling, leakage, or balance issues |
| Control MCU | Backup log memory, check heat profile |

---

## 🧪 7. In-Field Test Checklist

- [ ] EM field presence detected at capture zone  
- [ ] Audible harmonic tone or indicator LED active  
- [ ] Exhaust airflow is smooth and unrestricted  
- [ ] Filter insertion confirmed with audible click or lock  
- [ ] Residual radiation around unit measured at background or below  

---

## 🔄 Recommended Spares to Carry

- 2× Full Filter Stack  
- 1× HV Mesh Screen  
- 1× Mini bottle of 99% isopropyl  
- 1× Ultracap Fused Pack (swappable)  
- 1× Backup MCU SD card  
- Zip ties, cloths, anti-static bags

---

## ✅ Summary

- Filters are the **primary line of defense** against airborne isotopes  
- Proper handling prevents secondary exposure  
- A clean system runs quieter, pulls harder, and protects longer

---

**Next File:** `/hardware/Shielding-and-Housing-Options.md`  
→ Materials and design options for improving passive protection during high-field use

**© 2025 Bryce Wooster — Maintenance Is Protection**
