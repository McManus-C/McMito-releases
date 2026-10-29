# MCMITO 1.4.3 — 28 October 2026

MCMITO 1.4.3 is a maintenance release with one fix. On the Mitochondrial Oxidative Capacity tab, analysis settings could jump back to their defaults a few seconds after *Compute slopes*, and the computation then ran again by itself with those defaults. This no longer happens. The analysis engine is unchanged (algorithm version 2). Sessions and preferences from earlier versions open unchanged, and updating keeps your licence key and settings.

**Download:** `MCMITO_Setup_1.4.3.exe` from the *Assets* list below (the `manifest.txt` file is used by the in-app updater; you do not need it).
**Already on 1.1.0 or later?** Use *Settings → About → Check for updates* and the app installs 1.4.3 for you.

---

## Fix

- **Analysis settings no longer revert after Compute slopes.** In a long-running session, a few seconds after *Compute slopes* the *Analysis signal* could return to HbDiffCorrCal and *Min samples / slope* (and other changed settings) to their defaults. *Compute* then ran again with those values, which on data without a physiological calibration showed *Selected signal 'HbDiffCorrCal' is not available*. The cause was the page framework's response to a display element failing to draw: it undid the user's most recent changes one by one. MCMITO now blocks that roll-back. The element that failed keeps its previous content and your settings stay as you set them.
- **Display errors are now reported.** When a display element fails to draw, MCMITO shows a short notice and writes the element's name to `%USERPROFILE%\.mcmito\frontend_errors.log`. If you see the notice, please email that file to cmcman@essex.ac.uk; it tells us which element to fix.

## Compatibility

- Algorithm version 2 (unchanged). Results are identical to 1.4.2.
- Windows 10 / 11. Updating keeps your licence key, its expiry and all preferences.

## Citation

McManus, C. (2026). *MCMITO: Near-infrared spectroscopy analysis of skeletal-muscle mitochondrial oxidative capacity* (Version 1.4.3) [Computer software]. Zenodo. https://doi.org/10.5281/zenodo.22647702

Please also cite the method: Ryan TE, Erickson ML, Brizendine JT, Young HJ, McCully KK. Noninvasive evaluation of skeletal muscle mitochondrial capacity with near-infrared spectroscopy: correcting for blood volume changes. *J Appl Physiol* 2012;113(2):175–183. If you use Method 4 or the best-fit window, also cite Beever AT, Tripp TR, Zhang J, MacInnis MJ. NIRS-derived skeletal muscle oxidative capacity is correlated with aerobic fitness and independent of sex. *J Appl Physiol* 2020;129(3):558–568.

MCMITO is for research and educational use only and is not a medical device.
