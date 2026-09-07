<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="img/mcmito-logo-dark.png">
    <img src="img/mcmito-logo.png" alt="MCMITO" width="420">
  </picture>
</p>

<h3 align="center">Near-infrared spectroscopy analysis of skeletal-muscle mitochondrial oxidative capacity</h3>

<p align="center">
  <a href="https://github.com/McManus-C/McMito-releases/releases/latest"><img alt="Latest release" src="https://img.shields.io/github/v/release/McManus-C/McMito-releases?label=latest%20release&color=0e9f9f"></a>
  <a href="https://doi.org/10.5281/zenodo.22329660"><img alt="DOI" src="https://img.shields.io/badge/DOI-10.5281%2Fzenodo.22329660-blue"></a>
  <a href="https://www.mcmito.com"><img alt="Website" src="https://img.shields.io/badge/website-mcmito.com-0b3d5c"></a>
  <img alt="Platform" src="https://img.shields.io/badge/platform-Windows%2010%20%7C%2011-lightgrey">
</p>

---

## Latest release

| | |
|---|---|
| **Version** | **1.1.0** (28 August 2026) |
| **Download** | [MCMITO_Setup_1.1.0.exe](https://github.com/McManus-C/McMito-releases/releases/latest) — from the *Assets* list on the release page |
| **DOI** | [10.5281/zenodo.22329660](https://doi.org/10.5281/zenodo.22329660) |
| **Website** | [www.mcmito.com](https://www.mcmito.com) |
| **Contact / licence keys** | cmcman@essex.ac.uk |

**What's new in 1.1.0**

- **In-app updates.** *Settings → About → Check for updates* finds, verifies and installs new versions from this repository. Updates are cryptographically signed, and your licence key, its expiry date and all preferences are kept.
- **"As-displayed" results in the Excel export.** Three new sheets (`SlopeResults_Displayed`, `OcclusionSummary_Displayed`, `FitSummary_Displayed`) report the analysis exactly as shown on screen, honouring any occlusions or sets you excluded by hand. The existing everything-included sheets are unchanged.
- **First-run save-location prompt.** MCMITO asks where to save your files on first launch (default `Documents\MCMITO`); editable at any time under *Settings → Files*.
- **Fixes.** Saves no longer overwrite earlier files (`name (2).xlsx`, `name (3).xlsx`, …); the PDF report asks you to re-fit if exclusions changed after fitting; *Settings → Export preferences* now saves correctly in the installed app.

Full history: [CHANGELOG](#changelog) below.

> Already running **1.0.0a1**? That version predates the updater, so download and run the 1.1.0 installer once. It installs over the top and keeps your licence. From 1.1.0 onwards, updates arrive through the app.

---

## What MCMITO does

MCMITO is a desktop application that turns repeated-cuff NIRS recordings into reproducible measures of skeletal-muscle mitochondrial oxidative capacity. It implements the repeated arterial-occlusion method of Ryan et al. (2012): a series of brief cuff occlusions after a short exercise stimulus, the muscle oxygen consumption (mV̇O₂) measured from the haemoglobin slope during each occlusion, and the recovery of mV̇O₂ over time fitted with a mono-exponential curve to yield a rate constant (*k*) and time constant (*τ*).

<p align="center">
  <img src="img/hero-hbdiff-slopes.png" alt="Raw HbDiff trace across six repeated arterial occlusions, the desaturation slope of each occlusion highlighted and numbered 1 to 6; the slopes flatten as muscle oxygen consumption recovers" width="49%">
  <img src="img/hero-recovery-fit.png" alt="The six occlusion slopes plotted against time after exercise and fitted with a mono-exponential recovery curve, yielding the rate constant k" width="49%">
</p>

The whole pipeline runs locally on your machine. Your data never leave it.

### Capabilities

| | |
|---|---|
| **Automated occlusion detection** | Consensus detection finds every cuff occlusion in each set and places the markers for you, each with a confidence score you can accept, shunt or remove. |
| **Manual marking** | Place, move and remove set anchors and occlusion markers by hand on full-resolution traces, with instant feedback. |
| **Correction and calibration** | Ryan blood-volume correction and physiological 0–100 % calibration are built in. |
| **Per-occlusion slopes** | mV̇O₂ extracted from each occlusion, with a choice of slope window (full included window or steepest window), and automatic exclusion of low-R² and negative-slope occlusions. |
| **Recovery-curve fitting** | Mono-exponential fit of mV̇O₂ against time to *k* and *τ*, with standard errors and R² quality tiers, per set and combined. |
| **Exercise-stimulus metrics** | The exercise bout preceding each set is identified on TSI % and its key metrics extracted. |
| **Transparent and reproducible** | Every per-occlusion slope, exclusion and fit is visible and exportable. Each export records the software and algorithm version. |
| **Publication-ready exports** | One click to a full Excel workbook and a formatted PDF report. Save and reload a complete participant session (`.mcmito`) to pick up where you left off. |

---

## How it works

**1. Import.** Drag in your NIRS recording. Map channels once; MCMITO remembers the layout.

**2. Detect and mark.** Auto-detect occlusions per set, or place and refine markers by hand.

<p align="center">
  <img src="img/auto-detect-poster.jpg" alt="MCMITO Data Cleaning view: a raw HbDiff recording at full resolution with dashed set-anchor markers for four occlusion sets" width="90%">
</p>

**3. Correct and calibrate.** Apply blood-volume correction and physiological calibration to the signal.

**4. Fit.** Extract per-occlusion slopes and fit the recovery curve to *k* and *τ*. Every fitted line is shown alongside its mV̇O₂ and R², and exclusions are visible rather than hidden.

<p align="center">
  <img src="img/individual-occlusions.png" alt="Grid of every individual occlusion across four sets, each panel showing the signal, the fitted slope, its mV̇O₂ and R²" width="90%">
</p>

<p align="center">
  <img src="img/curve-fit-cycle-poster.jpg" alt="Recovery fit: per-occlusion mV̇O₂ points fitted with a mono-exponential recovery curve" width="60%">
</p>

**5. Export.** Save the Excel workbook and PDF report, and archive the full session.

<p align="center">
  <img src="img/exercise-phase-analysis.png" alt="Exercise phases for four sets identified and shaded on the TSI% trace" width="75%">
</p>

---

## Download and install

1. Open the [latest release](https://github.com/McManus-C/McMito-releases/releases/latest) and download **`MCMITO_Setup_<version>.exe`** from the *Assets* list. (The `manifest.txt` file alongside it is used by the app's own update check; you do not need it.)
2. Run the installer, accept the licence agreement when prompted and follow the steps. MCMITO installs per user, so no administrator rights are needed, and appears in the Start menu.
3. On first launch, choose where MCMITO should save your files (default `Documents\MCMITO`).

### Activating your licence

MCMITO requires a licence key, which is currently provided **free of charge** for research and educational use.

1. On first launch you will see an **activation screen** showing your **Machine ID**.
2. Copy the Machine ID and email it to **cmcman@essex.ac.uk**.
3. You will receive a **licence key** in return. Paste it into the activation screen and click **Activate**.

Each licence is tied to one computer and runs for a fixed period; the app warns you before it expires, and renewal is simply a new key for the same Machine ID. If you change computers, request a new key with your new Machine ID.

### System requirements

- Windows 10 or 11 (64-bit).
- No Python or other dependencies; everything is bundled.
- The app opens in its own window using Windows WebView2 (built into Windows 11 and most updated Windows 10). If WebView2 is unavailable it falls back to your default web browser.

### Updating

From version 1.1.0, use *Settings → About → Check for updates*. The app only installs releases published here that carry a valid signature and matching checksum. Your licence key and preferences are preserved.

---

## Built on the method

MCMITO implements the established repeated-cuff NIRS method for muscle mitochondrial capacity:

> Ryan TE, Erickson ML, Brizendine JT, Young HJ, McCully KK. Noninvasive evaluation of skeletal muscle mitochondrial capacity with near-infrared spectroscopy: correcting for blood volume changes. *Journal of Applied Physiology*. 2012;113(2):175–183. https://doi.org/10.1152/japplphysiol.00319.2012

The analysis pipeline has been validated against synthetic NIRS recordings with known recovery kinetics, so the pipeline is shown to recover the truth before it sees your data.

## How to cite

If you use MCMITO in your research, please cite the software together with the underlying method:

> McManus, C. (2026). *MCMITO: Near-infrared spectroscopy analysis of skeletal-muscle mitochondrial oxidative capacity* (Version 1.1.0) [Computer software]. Zenodo. https://doi.org/10.5281/zenodo.22329660

---

## Licence and intended use

MCMITO is **proprietary, licensed software** provided under an End-User Licence Agreement shown during installation. This repository holds installers and update manifests only; it does not contain source code.

MCMITO is intended for **research and educational use only and is not a medical device**. It is not for the diagnosis, prevention, monitoring, prediction, prognosis, treatment or alleviation of disease, and it has not been assessed by the MHRA or any other regulatory authority. You are responsible for independently validating any results you rely on.

## Changelog

### 1.1.0 — 28 August 2026

- New: in-app software updates (*Settings → About → Check for updates*).
- New: "as-displayed" results sheets in the Excel export (`SlopeResults_Displayed`, `OcclusionSummary_Displayed`, `FitSummary_Displayed`); the Metadata sheet records user-excluded occlusions.
- New: first-run save-location prompt (default `Documents\MCMITO`).
- Fixed: saves no longer overwrite earlier files of the same name.
- Fixed: PDF report staleness guard when exclusions change after fitting.
- Fixed: *Settings → Export preferences* now saves correctly in the installed desktop app.

### 1.0.0a1 — 25 June 2026

- First packaged release: standalone Windows application with native window, machine-bound time-limited licence activation, protected analysis core, installer and configurable output folder.
- Analysis platform: import and channel mapping, marker placement and auto-detection, blood-volume correction, physiological calibration, per-occlusion slope extraction with automatic low-R² and negative-mV̇O₂ exclusion, recovery-curve fitting (*k*, *τ*, SE, R²), exercise-stimulus metrics, Excel and PDF exports, and participant-session save/load.

---

## Contact

Chris McManus — University of Essex — cmcman@essex.ac.uk — [www.mcmito.com](https://www.mcmito.com)

© 2026 Chris McManus. All rights reserved.
