# MCMITO 1.4.1 — 12 October 2026

MCMITO 1.4.1 adds exercise-period and force-dose analysis to the Exercise Stimulus tab and reads recordings made with **McMito Live**, the companion acquisition and cuff-control app. The resting occlusion is now optional, saved sessions can be cropped and downsampled, and the Data Cleaning plots are much faster. Sessions and preferences from 1.3.0 open unchanged, and updating keeps your licence key and settings. (1.4.0 was an internal build and was not released.)

**Download:** `MCMITO_Setup_1.4.1.exe` from the *Assets* list below (the `manifest.txt` file is used by the in-app updater; you do not need it).
**Already on 1.1.0, 1.2.0 or 1.3.0?** Use *Settings → About → Check for updates* and the app installs 1.4.1 for you.

---

## Highlights

### Exercise periods and the Exercise Stimulus tab
- Exercise periods are now **markers**: one start and end pair per set ("S" for a stimulus test), placed, moved, nudged, snapped and removed on the Data Cleaning tab like any other marker (*Add Manually → Exercise periods*).
- A **Periods** card chooses where the periods come from: your markers, the protocol record of a McMito Live recording (exact bout times), the 1.3.0 fixed look-back, or signal variance. Estimated periods are written as markers, so every period is visible on the trace and can be corrected.
- For each period and channel the tab reports the 1.3.0 metrics plus the change from start to end, the change from the resting baseline (Rest markers), the desaturation slope, time to minimum, the mean of the last 2 s, and the post-exercise nadir before the first occlusion.

### Force dose (recordings with a force gauge)
- For McMito Live recordings made with a Tindeq Progressor: time under load (default threshold 10 % of MVC, or 10 % of the period's peak without an MVC), impulse (N·s), mean and peak force, % MVC, repetitions, duty cycle, coefficient of variation and fatigue index, with a force trace figure and an MVC table.
- **Dose–response:** an ordinary least-squares fit of a NIRS response (for example the change from start to end, or the post-exercise nadir) against a dose variable (impulse, time under load, mean % MVC or mean force), with r, r² and n. It needs at least three periods and is labelled exploratory.

### McMito Live recordings
- Opens `.mcmito` sessions recorded by McMito Live, including the force trace and the protocol events; exercise bouts become exercise-period markers when the file is opened.
- Imports McMito Live raw device files (`*.trainred.raw.csv`). Time stays on the session clock, so cuff and marker times from the matching `.mcmito` line up with the trace; tHb is derived as O2Hb + HHb and off-skin packets are skipped. Moxy raw files are refused with a message (they carry SmO2 and THb only).
- **Blood flow correction defaults to Method 4 (Beever, 2020) for McMito Live data.** McMito Live records the Train.Red's absolute O2Hb and HHb. With values that are positive throughout, the Ryan beta becomes O2Hb / tHb and Method 2 reduces exactly to HbDiff (Methods 1 and 3 approximately), so blood-volume shifts are not removed. Method 4 works on sample-to-sample changes and is unaffected by an absolute offset. The Ryan methods remain available; applying them to absolute data shows a caution, which is also recorded in the Excel metadata (`BFWarning`). A method saved with a session is always kept, and other data keep the default from *Settings → Defaults*.

### Analysis
- **The resting occlusion is optional.** *Compute slopes*, *Fit recovery curve* and the Excel export run without RestStart / RestEnd markers. The curve is then fitted from the occlusions alone; the rest-dependent settings are greyed out, and the two fit methods defined by the resting value (Fixed asymptote, Endpoint-anchored) are disabled with an explanation. The export records `RestingMeasure: none`.
- **Crop and Downsample work on saved sessions** (previously they needed a fresh import). Cropping keeps the markers inside the window; downsampling keeps the record's time origin and its markers. Both clear slopes and fits.

### Exports
- **Excel:** new sheets `ExercisePeriods`, `ExerciseMetrics`, `ForcePeriods`, `ForceReps`, `MVC`, `DoseResponse` and `ExerciseSummary`, and `ForceTrace` when *Settings → Files → Include the raw force trace* is on (default off). The 1.3.0 `ExercisePhases` sheet is kept for this release with the same table as `ExercisePeriods`.
- **PDF report:** an optional *Exercise and force* section (period table, force table, dose–response or force trace figure, methods line), ticked by default when force data exist.

### Faster and more reliable plots
- Marker overlays are drawn in one step. On a recording with 34 occlusions a full Data Cleaning render fell from about 12 s to 0.36 s, and moving a marker from about 2.4 s to 0.03 s.
- Plots no longer go blank after several re-renders ("Too many active WebGL contexts"). The full record is drawn as a decimated copy that keeps every local extreme; zooming or panning shows the visible window at full resolution, and a double-click restores the whole record.
- Zooming one plot moves the other four again (linked x-axes).

---

## Fixes
- *Check for updates* now says when nothing has been published or the server returns an error, instead of always reporting that it could not reach the update server.
- A session opened at launch (`MCMITO.exe --open <file.mcmito>`, as McMito Live does when it hands over a recording) keeps the blood flow correction method saved with it.

## Changes
- A saved session can be opened at launch with `MCMITO.exe --open <file.mcmito>`.
- Licence keys are issued per product. Existing MCMITO keys remain valid; a McMito Live key does not open MCMITO, and the reverse.
- The packaged app's self-test (`MCMITO.exe --selftest`) checks every module and saves its report to `%USERPROFILE%\.mcmito\selftest.txt`, which helps if support is needed.
- Algorithm version 2 (unchanged). Re-running the 10-participant validation cohort gave numeric outputs identical to 1.3.0.

## Compatibility
- Sessions and preferences from 1.3.0 open unchanged. The `.mcmito` format gains optional members for McMito Live recordings (force trace and protocol events). Open sessions saved by 1.4.1 in 1.4.1 or later.
- Windows 10 / 11. Updating keeps your licence key, its expiry and all preferences.

## Citation
McManus, C. (2026). *MCMITO: Near-infrared spectroscopy analysis of skeletal-muscle mitochondrial oxidative capacity* (Version 1.4.1) [Computer software]. Zenodo. https://doi.org/<DOI>

Please also cite the method: Ryan TE, Erickson ML, Brizendine JT, Young HJ, McCully KK. Noninvasive evaluation of skeletal muscle mitochondrial capacity with near-infrared spectroscopy: correcting for blood volume changes. *J Appl Physiol* 2012;113(2):175–183. If you use Method 4 or the best-fit window, also cite Beever AT, Tripp TR, Zhang J, MacInnis MJ. NIRS-derived skeletal muscle oxidative capacity is correlated with aerobic fitness and independent of sex. *J Appl Physiol* 2020;129(3):558–568.

MCMITO is for research and educational use only and is not a medical device.
