# Solaris Deep-Space Mission Control UI Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Overhaul the Solar System UI into a high-precision aerospace mission control console featuring real-time orbital calculations, a bottom telemetry scrub-deck, an audio engine, and a deep-space planetary dossier.

**Architecture:** Single-file architecture in `index.html`. CSS handles obsidian glassmorphism, responsive cyber-grid layouts, and monospace telemetry meters. JavaScript manages Web Audio API synth nodes, live Keplerian velocity math, camera flight interpolation, and keyboard shortcuts.

**Tech Stack:** Three.js (ES Module via CDN), Vanilla JavaScript, CSS3 (backdrop-filter, CSS grid, variables), Web Audio API, Google Fonts (JetBrains Mono & Bricolage Grotesque).

**Spec:** `docs/superpowers/specs/2026-11-07-mission-control-ui-design.md`

## Global Constraints
- Single-file deliverable: everything is contained within `index.html`.
- Zero external audio/asset dependencies: ambient audio and clicks must use Web Audio API oscillators.
- Preserves all NASA photographic textures, bump maps, rings, asteroid belt, and moon meshes.
- 100% responsive and accessible (keyboard shortcuts, high contrast, aria labels, reduced motion).

## Review Focus
1. Audio autoplay policy: AudioContext must be resumed on first user interaction to comply with browser autoplay protections.
2. Real-time telemetry performance: Orbital calculations (distance, velocity, light transit) must run without allocating GC-heavy objects in `animate()`.
3. Cinematic tour interrupted gracefully: User mouse drag or planet click must immediately exit cinematic mode without camera jerking.
4. Mobile / portrait layout: Telemetry drawer must collapse gracefully to bottom sheet without obscuring bottom command dock.
5. Touch targets & contrast: All buttons >= 40px hit area, text contrast >= 4.5:1 against glass backdrops.

---

### Task 1: Mission Control Obsidian Design System & Layout Structure
**Files:**
- Modify: `index.html:10-150`

- [ ] **Step 1: Update CSS Design System**
  Add JetBrains Mono font import, obsidian color variables (`--bg: #03050a`, `--hud-glass: rgba(8, 12, 22, 0.75)`, `--cyan: #00f0ff`, `--amber: #ffb12e`), cyber-corner borders, and micro-grid layout classes.
- [ ] **Step 2: Replace HUD HTML Skeleton**
  Build the top command bar, bottom scrub-deck container, and right telemetry drawer shell with semantic data attributes.
- [ ] **Step 3: Verify visual layout in browser**
  Check that the top bar, bottom dock, and canvas render cleanly without overflow or broken styles.

---

### Task 2: Top Command HUD & Web Audio Engine
**Files:**
- Modify: `index.html` (CSS & JS)

- [ ] **Step 1: Implement Live UTC Epoch Clock & Flight Tracker**
  Update top bar with live UTC timestamp (`YYYY-MM-DD HH:mm:ss UTC`), camera distance from Sun (AU / M km), and target coordinates.
- [ ] **Step 2: Add Web Audio API Synthesizer**
  Implement self-contained audio engine with low-frequency spatial ambient drone (`55 Hz` dual oscillator) and high-pitch tactical click synthesizer for UI buttons and planet selection.
- [ ] **Step 3: Implement Layer Toggles**
  Add interactive toggle buttons for Orbits visibility, Asteroid Belt visibility, and Moons visibility.

---

### Task 3: Bottom Orbital Scrub-Deck & Keyboard Command Interface
**Files:**
- Modify: `index.html` (CSS & JS)

- [ ] **Step 1: Build Tactical Planet Carousel**
  Display sequential orbital pills with planet symbols, color rings, distance ranks, and active highlight indicators.
- [ ] **Step 2: Implement Time Speed Multipliers & Scrub Bar**
  Add play/pause toggle button, speed multiplier buttons (`0.25×`, `1×`, `4×`, `16×`), and interactive progress scrub.
- [ ] **Step 3: Wire Global Keyboard Shortcuts**
  Map keys `1`–`8` to planets, `0` to Sun, `Space` to Play/Pause, `C` to Cinematic Tour, `O` to Overview, and `Esc` to deselect.

---

### Task 4: Right Deep-Space Telemetry Dossier with Live Physics Math
**Files:**
- Modify: `index.html` (JS & CSS)

- [ ] **Step 1: Real-time Keplerian Telemetry Calculations**
  Calculate instantaneous distance from Sun, orbital velocity ($v = \sqrt{GM/r}$ in $km/s$), light travel transit time from Sun, and solar flux ($W/m^2$).
- [ ] **Step 2: Segmented Drawer Views**
  Structure drawer into tabs/sections: Telemetry & Dynamics, Physical Specifications, Atmosphere Breakdown (visual progress bar), and Historic Mission Exploration log.
- [ ] **Step 3: Sliding Animation & Mobile Sheet Adaptation**
  Animate drawer with exponential ease-out; adapt into a compact drawer on viewports < 768px.

---

### Task 5: Cinematic Tour Mode & Visual Polish
**Files:**
- Modify: `index.html` (JS)

- [ ] **Step 1: Implement Cinematic Auto-Tour Sequence**
  Sequentially fly camera between planets at customizable intervals, displaying each planet's telemetry before smoothly transitioning to the next.
- [ ] **Step 2: Smooth Camera Transitions and Interruption Handling**
  Ensure any user drag, pan, or click instantly yields camera control without jitter.
- [ ] **Step 3: Run Impeccable Mechanical Detector**
  Run `& 'C:\Users\Gian Karlo\.gemini\config\skills\impeccable\scripts\impeccable.cmd' detect --json index.html` to verify zero UX/contrast/layout issues.
