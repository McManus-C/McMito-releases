# MCMITO 1.4.2 — 19 October 2026

MCMITO 1.4.2 is a maintenance release prompted by analysing McMito Live recordings with two sets of 17 occlusions. Session files saved by McMito Live now open (1.4.1 could not read them), the sensor's "no reading" zeros load as blanks, the Protocol boxes now drive the analysis, cuff markers can be loaded from a McMito Live session, the per-occlusion fit figure keeps its panel size for long protocols, and the Data Cleaning tab is easier to work in. The analysis engine is unchanged (algorithm version 2). Sessions and preferences from earlier versions open unchanged, and updating keeps your licence key and settings.

**Download:** `MCMITO_Setup_1.4.2.exe` from the *Assets* list below (the `manifest.txt` file is used by the in-app updater; you do not need it).
**Already on 1.1.0 or later?** Use *Settings → About → Check for updates* and the app installs 1.4.2 for you.

---

## Fixes

- **McMito Live session files open.** MCMITO 1.4.1 could not open any `.mcmito` file saved by McMito Live and showed *Session load failed: 'utf-8' codec can't decode byte 0x80 …*. McMito Live stores the recording inside the file in a compact table format (parquet), and the reader for it was missing from the 1.4.1 installer. It is now included. Files saved by MCMITO itself were not affected.
- **Sensor dropouts are blanks, not zeros.** A Train.Red FYER sends 0 for a channel it has no reading for: SmO2 while the sensor settles after it is put on and when it lifts off, and O2Hb / HHb for about the first second. For McMito Live recordings (a `.mcmito` it saved or one of its raw device files) these zeros now load as blanks, so the traces no longer drop to 0 and a 0 can never enter a slope or a mean. OxySoft and Train.Red app exports are unchanged, because they record changes from a baseline, where 0 is a real value.
- **Updating from inside MCMITO no longer stalls.** Updating from 1.4.1 could stop at *Closing applications…* behind a .NET *Unhandled exception … 'master'* message. The installer now closes MCMITO itself and reopens it when the update is finished.
- **Downsampling keeps a gap a gap.** A blank sample no longer blanks several seconds of the downsampled trace; only the samples it falls in are blank. Recordings without blanks downsample exactly as before.
- **The Protocol boxes now drive the analysis.** In earlier versions, editing *Sets*, *Occlusions / set*, *Cycle period* or *Occlusion duration* after the data were loaded changed only the marker counter. Auto-detect still looked for the default 6 occlusions per set, and the slope window, the Method 1 windows, the fit overlay and the Excel metadata kept the values from loading. Every valid edit now applies at once. Markers are kept; slopes and fits computed under the previous protocol are cleared, with a message.
- **The per-occlusion fit figure keeps its panel size.** With many occlusions (for example 2 × 17) the panels shrank to thin strips. Panels and gaps now keep the size of a 4 × 6 session, whose figure is unchanged; the figure grows with the number of rows, and each set starts on a new row so occlusion *k* of every set sits in the same column.

## New

- **Cuff markers from a McMito Live session.** After importing a McMito Live raw device file (`*.trainred.raw.csv`), a box under the upload offers *Load cuff markers from .mcmito*. The `.mcmito` saved with that recording supplies the markers McMito Live placed at the cuff commands (calibration, set anchors, occlusions) on the same session clock, so auto-detect is not needed. The file must come from the same recording. The Protocol boxes are set from the markers and from the protocol McMito Live ran.

## Interface

- **Data Cleaning controls scroll on their own.** The left panel stays under the header and fits the window. Scrolling it no longer moves the plots, and scrolling the plots no longer moves it.
- **Fixed hover readout.** The floating hover box, which covered the trace while placing markers, is replaced by a readout in each plot's title strip (time and value) and a dotted vertical guide at the cursor. Placing markers by clicking is unchanged.

## Compatibility

- Algorithm version 2 (unchanged). Results change only for a McMito Live recording with a sensor dropout (a 0) inside an analysis window; all other data give identical results.
- If you analysed a recording in 1.4.1 and changed the Protocol boxes after loading it, the slopes, fits and export used the protocol from loading time. Re-run that analysis in 1.4.2 after checking the Protocol boxes.
- Windows 10 / 11. Updating keeps your licence key, its expiry and all preferences.

## Citation

McManus, C. (2026). *MCMITO: Near-infrared spectroscopy analysis of skeletal-muscle mitochondrial oxidative capacity* (Version 1.4.2) [Computer software]. Zenodo. https://doi.org/10.5281/zenodo.22647702

Please also cite the method: Ryan TE, Erickson ML, Brizendine JT, Young HJ, McCully KK. Noninvasive evaluation of skeletal muscle mitochondrial capacity with near-infrared spectroscopy: correcting for blood volume changes. *J Appl Physiol* 2012;113(2):175–183. If you use Method 4 or the best-fit window, also cite Beever AT, Tripp TR, Zhang J, MacInnis MJ. NIRS-derived skeletal muscle oxidative capacity is correlated with aerobic fitness and independent of sex. *J Appl Physiol* 2020;129(3):558–568.

MCMITO is for research and educational use only and is not a medical device.
