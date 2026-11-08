# Relativistic Odyssey

An interactive, browser-based educational visualisation of Special Relativity. Three connected HTML pages guide the user from first principles through to an immersive 3D interstellar journey, with physically accurate relativistic aberration, Doppler colour shift, and relativistic beaming rendered in real time via Three.js and WebGL.

---

## Project objective

To make the counter-intuitive consequences of special relativity — time dilation, length contraction, relativistic aberration, and the Doppler effect — tangible and explorable without prior knowledge of physics or mathematics.

---

## The three pages

| File | Purpose |
|------|---------|
| `1_Relativity_Dashboard.html` | Educational introduction to special relativity. Covers time dilation, length contraction, aberration, and Doppler shift with equations and an interactive velocity control. Links to both simulators. |
| `2_Relativistic_Universe.html` | Interactive static simulator. Adjust the observer's velocity from 0 to 0.9999c with a slider or preset buttons and observe the starfield transform in real time. Toggle aberration, Doppler colour, and relativistic beaming independently. |
| `3_Relativistic_Journey.html` | Animated interstellar journey. Configure destination, cruise velocity, and animation duration; then fly from Earth to a star system and compare elapsed time in the Earth frame versus the spaceship frame. A three-phase animation (ramp-up / cruise / ramp-down) illustrates how aberration develops and dissolves. |

Keep all three HTML files in the same directory. They link to each other by filename.

---

## Main physics concepts demonstrated

### Lorentz factor (γ)

The Lorentz factor governs the magnitude of all relativistic effects:

```
β = v / c
γ = 1 / √(1 − β²)
```

γ = 1 at rest and grows without bound as v → c.

### Time dilation

A clock moving at speed v runs slow compared to a stationary clock:

```
Δt′ = Δt / γ
```

Δt is the coordinate time between two events in the observer's rest frame; Δt′ is the proper time measured by the moving clock. Because γ ≥ 1, Δt′ ≤ Δt. The elapsed time measured between the same pair of events is legitimately frame-dependent.

### Length contraction

A ruler of proper length L at rest appears contracted along the direction of motion:

```
L′ = L / γ
```

In the journey simulator, the Earth–destination distance d (ly) contracts to d′ = d / γ in the spaceship frame, reducing the proper time needed to complete the trip.

### Relativistic aberration

A moving observer perceives photon arrival angles differently from a stationary observer. Stars from across nearly the entire sky converge toward the forward direction as β → 1:

```
cos θ′ = (cos θ + β) / (1 + β cos θ)
```

θ is the rest-frame angle from the forward axis; θ′ is the apparent angle for the moving observer.

### Relativistic Doppler shift and beaming

The relativistic Doppler factor D modifies both the frequency and apparent brightness of incoming light:

```
D = 1 / [γ (1 − β cos θ)]
```

- **Forward stars (θ ≈ 0):** D > 1, photons are blueshifted and amplified. Blackbody temperature scales as T_obs = T_rest × D. At very high velocities the forward cone turns intense blue-white.
- **Rearward stars (θ ≈ π):** D < 1, photons are redshifted and dimmed.
- **Relativistic beaming:** Apparent flux from forward sources scales approximately as D^2.5–D^3, so at 0.99c the forward region is orders of magnitude brighter than at rest.

### Earth frame vs. spaceship frame (Journey page)

**Earth Frame**: An observer on Earth watches the ship depart and arrive. The journey takes the full configured animation duration. The starfield is undistorted.

**Relativistic Frame**: The crew aboard the ship experience time passing at the proper rate τ = t_E / γ. The journey animation runs for t_E / γ wall-clock seconds. Aberration builds over the first 40% of the animation, holds at peak cruise during the middle 20%, and gradually dissolves over the final 40%.

---

## How to launch

The project has no build step or external dependencies beyond an internet connection (Three.js is loaded from jsDelivr CDN).

1. Open a terminal in the project folder.
2. Start a local web server:

   ```powershell
   python -m http.server 8000
   ```

   If `python` is not available, try `py -m http.server 8000`.

3. Open `http://localhost:8000/1_Relativity_Dashboard.html` in a modern browser (Chrome, Edge, Firefox, or Safari 16+).
4. Use the navigation links at the top of each page to move between the Dashboard and the two simulators.
5. Stop the server with **Ctrl+C**.

Serving over HTTP is recommended. Browsers restrict ES module loading when files are opened directly with `file://`.

---

## Controls and interactive features

### Relativity Dashboard (`1_Relativity_Dashboard.html`)

- **Velocity slider and presets** — adjust velocity from 0.0c to 0.9999c (or quick-jump via presets) and observe real-time recalculation of the Lorentz factor γ, dilation factor, forward Doppler factor, and half-sky aberration cone angle.
- **Interactive Twin Paradox Trip Calculator** — enter any journey duration in the Earth frame (years) to dynamically calculate ship proper time (τ) and the elapsed twin gap (Δt).
- **Interactive Length Contraction Calculator** — enter any proper distance (ly) or select star presets (Alpha Centauri, Sirius, Vega) to see the contracted distance (L′) and percentage contraction.
- **Interactive Doppler Wavelength Calculator** — set rest wavelength (λ₀ nm) with color presets (UV, Green, Red, Infrared) to compute forward and rearward shifted wavelengths with live spectral classification badges.
- **Navigation cards and pills** — launch directly into either simulator.

### Relativistic Universe (`2_Relativistic_Universe.html`)

- **Velocity slider** (0 – 0.9999c) — continuously updates the starfield. Smooth, no abrupt jumps.
- **Preset buttons** — jump to 0.0c, 0.25c, 0.50c, 0.90c, 0.99c, 0.9999c.
- **Physical effect toggles** — Relativistic Aberration, Relativistic Doppler Shift, Relativistic Beaming, each can be toggled independently.
- **Camera views** — FRONT (cockpit), REAR, SIDE, FREE (orbital).
- **Environment toggles** — 3D Spaceship, Cockpit Canopy, Forward Vector Guide.
- **Starfield density** slider (1 000 – 15 000 stars).
- **Rest wavelength** (λ₀ nm) selector with live spectral readout for forward and rearward shifted wavelengths.
- **Info panel** — physics equations and explanations.
- **Reset** — restores all defaults.

### Relativistic Journey (`3_Relativistic_Journey.html`)

- **Reference frame selector** — Earth Frame or Relativistic Frame.
- **Velocity slider** (0.005c – 0.9999c) with preset pills.
- **Destination selector** — Alpha Centauri A, Barnard's Star, Sirius A, Vega, or a custom light-year distance.
- **Earth animation duration** (5 – 120 s) — sets the wall-clock length of the Earth-frame animation; the ship-frame duration is calculated as T_Earth / γ.
- **Start / Pause / Reset** — control the flight.
- **Timeline scrubber** — click or drag to any point in the journey.
- **Camera modes** — Chase, Cockpit (first-person), Side, Free.
- **Arrival debrief modal** — summarises Earth time, ship proper time, velocity, and time saved.
- **Physics drawer** — equations and explanations.

---

## Technologies used

- HTML5, CSS3, JavaScript (ES2020 modules)
- [Three.js 0.160.0](https://threejs.org/) — 3D scene, WebGL renderer, OrbitControls
- Loaded from jsDelivr CDN via browser import maps; no bundler required
- WebGL (required) — hardware-accelerated point sprites with custom vertex/fragment shaders

The starfield is rendered as a `THREE.Points` cloud with a custom `ShaderMaterial`. Each star is computed on the CPU for every frame update: its rest-frame spherical coordinates (θ, φ) are transformed by the aberration formula, its apparent colour is computed from its Doppler-shifted blackbody temperature, and its brightness is scaled by the beaming factor. The GPU shader adds Gaussian soft-core glow and a halo bloom effect.

---

## Assumptions and limitations

- **Constant-velocity idealisation**: The journey page computes elapsed times using the special-relativistic formulae for constant-velocity travel (β = const, γ = const). Real interstellar travel would require prolonged acceleration and deceleration phases with a continuously varying γ. The simulation is an educational visualisation, not a trajectory calculation.
- **No gravitational effects**: Special relativity only; general relativistic corrections (gravitational time dilation, curved spacetime) are not modelled.
- **No propulsion model**: The simulation does not address how the ship reaches cruise velocity. The 40% / 20% / 40% aberration ramp is an animation convenience, not a detailed acceleration profile.
- **Stellar positions are fixed**: Stars are placed isotropically on a celestial sphere of fixed radius. Proper motion and parallax are not modelled.
- **Blackbody approximation**: Stellar colours are computed from an effective blackbody temperature using the Planckian locus approximation (Neil Bartlett / Tanner Helland algorithm), not from full spectral energy distributions.
- **Numerical limits**: β is capped at 0.9999999 to avoid singularities in γ. The Doppler temperature is capped at 2 000 000 K to avoid numerical overflow in the colour calculation.
- **Performance**: The simulation targets 60 fps on a modern desktop GPU. Very high star counts (> 10 000) may reduce frame rate on integrated graphics.

---

## File structure

```
Project 2/
├── 1_Relativity_Dashboard.html    ← Educational introduction (this project's entry point)
├── 2_Relativistic_Universe.html   ← Static relativistic starfield simulator
├── 3_Relativistic_Journey.html    ← Animated interstellar journey simulator
├── README.md                      ← This document
├── PROJECT_PROMPTS.md             ← Documented prompts across all development rounds
└── backups/                       ← Historical recovery baselines and archives
```
