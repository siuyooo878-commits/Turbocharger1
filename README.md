# John's Engineering Disasters — Ep.01: The Turbocharger

## Run
Browser modules + large assets need HTTP (not file://):
    cd project && python3 -m http.server 8000   → open http://localhost:8000
Needs internet once for Three.js 0.180.0 (jsDelivr import map) and, for export, mp4-muxer 5.1.3. Use desktop Chrome/Edge.

## Assets (assets/…)
models/: 2011_lexus_lfa.glb (hero car, wheels spin), 2025_bmw_m4_gt3_evo_g82.glb (the "suspicious BMW"), basic_turbo_charger.glb (turbine/compressor wheels, housings, spun on a shared axis).
environments/: autoshop_01_2k.hdr (workshop), parking_garage_2k.hdr (hotel, lab), zwartkops_curve_morning_2k.hdr (dyno).
audio/: narration.m4a (audio track extracted from lv_0_20261018174359.mp4), LFA rev/fly-by, whooshes, metal-drop. videoplayback.m4a is copied but NOT used (content not identified).

## Timeline
All timing is data in SCRIPT at the top of index.html (scene start times). Scenes A–M follow pauses measured in narration.m4a;
N and O are estimated because the narration file ends (~108 s) before the last lines. Edit times in "Scene timing", or upload a longer
narration file (stretches only the tail scenes M–O). Seeking is deterministic: every frame is a pure function of time.

## Export
"Export" renders every frame at 1080×1920/30 fps (WebCodecs H.264) with an offline-rendered audio mix (AAC) muxed by mp4-muxer. Frame-by-frame, slower than real time, ~120 MB in memory. If the browser lacks WebCodecs it says so; nothing is silently downgraded.

## Honest limitations
Not rendered/tested in the build sandbox (no network/GPU there): only a syntax check was run. Expect to tune camera keyframes after first viewing.
Procedural pieces: John and other people, engine, hoist, hotel props, cylinder cutaway, pipes/intercooler. Hood is not opened (a dark cavity patch marks the removed engine). The BMW GT3 model is a race car standing in for the modified sedan; BMW-aggressive-cam audio does not exist, so the LFA recording is lowered/pitch-shifted with a lumpy modulation. Warning beeps and the turbo whine are synthesized. All graphs are labelled ILLUSTRATIVE.
