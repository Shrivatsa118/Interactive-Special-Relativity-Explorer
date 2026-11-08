# Project Development Prompts — Relativistic Odyssey

This document records the prompts used throughout the iterative development and refinement of the Relativistic Odyssey project, organized by improvement round.

---

## Round 1 — Initial Construction

*Context: Initial implementation of the special relativity 3D simulators.*

### Prompt 1.1: Core Relativistic Simulation Prototype (Reconstructed from codebase history)
> **Role / Context**: Senior Computational Physicist & Three.js WebGL Engineer  
> **Task**: Create an interactive 3D browser simulation of Special Relativity named `Relativistic_Universe.html`.  
> **Requirements**:
> - Real-time 3D starfield using Three.js with uniform isotropic distribution on a celestial sphere.
> - Implement relativistic aberration via $\cos \theta' = (\cos \theta + \beta) / (1 + \beta \cos \theta)$ along the $+Z$ axis.
> - Compute relativistic Doppler factor $D = 1 / [\gamma (1 - \beta \cos \theta)]$ and shift stellar blackbody temperatures ($T_{obs} = T_{rest} \times D$).
> - Model relativistic beaming (headlight effect) scaling starlight flux.
> - Provide cockpit, stern, starboard, and orbital camera perspectives, physical toggles, and velocity slider up to $0.9999c$.

### Prompt 1.2: Animated Interstellar Journey Prototype (Reconstructed from codebase history)
> **Role / Context**: Scientific Simulation & Spaceflight UI Developer  
> **Task**: Build `Relativistic_Journey.html` to visualize interstellar flight from Sol to target star systems (e.g. Alpha Centauri).  
> **Requirements**:
> - Distinguish Earth reference frame from Ship relativistic reference frame.
> - Implement dual clock telemetry: coordinate time ($t_E = d/v$) vs ship proper time ($\tau = t_E / \gamma$).
> - Illustrate length contraction ($d' = d / \gamma$).
> - Implement a 3-phase journey profile (aberration ramp-up 40%, peak cruise 20%, ramp-down deceleration 40%).
> - Include timeline scrubbing, destination selector, and an arrival debrief modal.

---

## Round 2 — Architecture, Refinement & Visual Consistency

*Context: Unifying the standalone pages into a cohesive three-page educational suite with consistent navigation and theory companion.*

### Prompt 2.1: Three-Page Architecture & Physics Refinement (Actual User Prompt)
```markdown
# PROJECT REFINEMENT — RELATIVISTIC ODYSSEY
## Three-Page Architecture, Visual Consistency and Physics Refinement

The project must contain three connected HTML pages:
1. 1_Relativity_Dashboard.html
2. 2_Relativistic_Universe.html
3. 3_Relativistic_Journey.html

Also update the project's existing Markdown documentation file (README.md).

CRITICAL RULE: PRESERVE EXISTING WORK
- Inspect all existing HTML files.
- Compare Relativistic_Universe.html and Relativistic_Journey.html.
- Reuse the existing Universe implementation wherever possible.
- Do not replace entire files when a targeted modification is sufficient.

PART 1 — RELATIVISTIC UNIVERSE (2_Relativistic_Universe.html)
- Preserve existing 3D environment, spaceship, starfield, velocity controls, and HUD.
- Refinement: directional blue shift and brightness in forward cone as velocity approaches c.

PART 2 — RELATIVISTIC JOURNEY (3_Relativistic_Journey.html)
- Reuse Universe starfield implementation (aberration, Doppler color, brightness).
- Ensure smooth transitions across the 40% / 20% / 40% flight profile.
- Preserve the two reference frames (Earth frame vs Relativistic frame).

PART 3 — RELATIVITY DASHBOARD (1_Relativity_Dashboard.html)
- Educational introduction to Special Relativity.
- Sections on Intro, Time Dilation (with interactive slider), Length Contraction, Aberration & Doppler.
- Connect all three pages with prominent navigation.

PART 4 — DESIGN CONSISTENCY & PART 5 — README DOCUMENTATION
```

### Prompt 2.2: Controlled Duplicate Cleanup (Actual User Prompt)
```markdown
## 7. DUPLICATE FILE IDENTIFICATION AND CAREFUL CLEANUP

The project directory now contains additional HTML files that appear to be duplicates following the recent refinement.
I want the project directory cleaned up, but file preservation takes priority over cleanup.

A. Identify all files (Numbered, Unnumbered, Backups .bak).
B. Determine necessary files (1_Relativity_Dashboard.html, 2_Relativistic_Universe.html, 3_Relativistic_Journey.html, README.md).
C. Cleanup rules: preserve original source files and useful recovery backups. Do not delete .bak files merely because they are older.
D. Safe deletion procedure: create separate backup folder, copy candidate duplicates, verify copies, wait for approval.
Do not delete or overwrite the original unnumbered Universe or Journey files during this process.
E. Final directory verification report.
```

---

## Round 3 — Authoritative Restoration, Audit & Submission Packaging

*Context: Restoring authoritative source baseline, full requirement audit, interactive expansion, and final packaging.*

### Prompt 3.1: Targeted Restoration of Universe Baseline (Actual User Prompt)
```markdown
# TARGETED FILE REPLACEMENT — RELATIVISTIC UNIVERSE

I am providing an original HTML file named `Relativistic_Universe backup.html`.
This file contains the original, working implementation of the Relativistic Universe simulator.
I want you to use this supplied file as the authoritative source for restoring the active Universe page.

1. Replace the active Universe implementation:
Target file: 2_Relativistic_Universe.html
Source file: Relativistic_Universe backup.html
- Replace contents of 2_Relativistic_Universe.html with the supplied original file.
- Preserve target filename and location.
- Preserve original JavaScript, shaders, physics, controls, and styling exactly.

2. Preserve the rest of the project:
Do not modify 1_Relativity_Dashboard.html, 3_Relativistic_Journey.html, README.md.

3. Protect existing files:
Create backup of current 2_Relativistic_Universe.html before replacing.
```

### Prompt 3.2: Controlled Root Cleanup Execution (Actual User Prompt)
```markdown
Proceed with the following carefully controlled cleanup.
1. Delete Relativistic_Universe.html.
2. Delete 2_Relativistic_Universe.html.bak.
3. Retain Relativistic_Journey.html because the restored Universe page currently references this filename.
4. Do not modify any HTML file during this cleanup.
5. Do not delete or modify any other original files or backups.
6. Verify that all three numbered HTML pages remain present and intact.
7. Report the final directory contents.
```

### Prompt 3.3: Final Project Completion & Submission Packaging (Actual User Prompt)
```markdown
# FINAL PROJECT COMPLETION — RELATIVITY INTERACTIVE HTML PROJECT

Bring the project into full compliance with assignment requirements, verify everything, document improvements, and prepare final submission package:
1. Preserve existing project (do not rebuild, create backups).
2. Audit assignment requirements (standalone, 3 distinct categories, min 5 interactions per page, responsive design, functional testing).
3. Physics and mathematical accuracy verification (Lorentz factor, time dilation, length contraction, aberration).
4. Document three improvement rounds.
5. Create PROJECT_PROMPTS.md.
6. Update README.md if necessary.
7. Create FINAL_SUBMISSION folder and Relativity_Interactive_Project_FINAL.zip (< 10 MB, verified).
8. Provide Final Verification Report table (PASS / FAIL / NOT VERIFIED).
```
