# Solaris Deep-Space Mission Control (UI Overhaul Design)

**Date:** 2026-11-07  
**Approach:** Direction 1 — Deep-Space Telemetry Console (SpaceX / NASA Mission Control)  
**Status:** Pending Approval  

---

## 1. Intent & Purpose
Elevate the Solar System Explorer UI from a basic floating-widget demo into an award-winning, $10,000-grade interactive deep-space telemetry console. The visual language blends aerospace mission control dashboards with luxury dark-mode aesthetics (obsidian glass, hairline cyber-grids, mono telemetry typography, real-time astronomical computations).

---

## 2. Visual Architecture & Design System

### A. Color & Surface
- **Base Canvas:** Deep obsidian space (`#03050a`).
- **Glass Surfaces:** High-blur acrylic (`rgba(8, 12, 22, 0.72)`, `backdrop-filter: blur(24px) saturate(160%)`).
- **Hairlines & Dividers:** High-precision borders (`1px solid rgba(255, 255, 255, 0.09)`).
- **Telemetry Accents:** Primary Cyan (`#00f0ff`), Amber Alert (`#ffb12e`), Critical Status (`#38ef7d`).
- **Data Monospace:** JetBrains Mono / Space Mono for all live numbers, coordinates, and telemetry tickers.

### B. Top Command HUD
- **System Header:** `SOLARIS // DEEP SPACE OBSERVATORY v4.2` + Live UTC Epoch Clock.
- **Flight Dynamics Readout:** Live camera distance (AU/km), field-of-view, active coordinate tracking $(X, Y, Z)$.
- **Quick Controls:**
  - View Layer Filters: `Orbits` [ON/OFF], `Asteroid Belt` [ON/OFF], `Moons` [ON/OFF].
  - `Cinematic Tour` button: Automatic orbital fly-through sequence.
  - `Overview` button: Camera reset.
  - `Audio` toggle: Synthesized ambient space drone + mechanical frequency clicks (Web Audio API, muted by default).

### C. Bottom Orbital Scrub-Deck
- **Time Controls:** Play / Pause toggle, preset speed multipliers (`0.5×`, `1×`, `4×`, `16×`), and precision scrub slider.
- **Sequential Planet Carousel:** Tactical pill selector with planet symbols, color indicators, distance order, and keyboard shortcuts (`1`–`8`).
- **Keyboard Assist Badge:** `[1-8] SELECT | [SPACE] PAUSE | [C] TOUR | [O] OVERVIEW | [ESC] DESELECT`.

### D. Right Telemetry Dossier (The $10k Console)
- **Designation Header:** Mission ID (e.g., `MARS // SOL-IV`), classification badge, and coordinate vector.
- **Segmented Sub-consoles:**
  1. **Orbital Telemetry:** Real-time distance from Sun, calculated orbital velocity ($km/s$), light travel time from Sun (e.g., Earth: 8.31 min, Neptune: 4.16 hrs), solar irradiance ($W/m^2$).
  2. **Physical Specs:** Diameter, mass ($M_\oplus$), surface gravity, day length, escape velocity, temperature range.
  3. **Atmospheric Profile:** Visual multi-segment gas proportion bar with chemical notation ($CO_2$, $N_2$, $O_2$, $CH_4$).
  4. **Exploration Dossier:** Historic spacecraft missions, landing craft, and active orbital probes.

### E. Audio Engine (Zero External Assets)
- Built entirely with browser **Web Audio API** oscillators:
  - Low-frequency resonant cosmic ambient drone ($55\text{ Hz} \to 110\text{ Hz}$).
  - Soft crisp sine blips on hover/selection ($800\text{ Hz}$ fast envelope).
  - 100% self-contained, no network lag or missing mp3 files.

---

## 3. Scope & Files Touched
- Single file update: [index.html](file:///c:/College%20Days/PORTFOLIOOOOO/proj/SolarSystem/index.html).
- Self-contained in existing Three.js + Vanilla JS stack.
