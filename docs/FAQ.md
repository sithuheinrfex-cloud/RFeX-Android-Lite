# FAQ and Support — RFeX Drive Lite

**What does Lite cost?** Planned as free to install with small advertisements on noncritical idle screens. No account or ad watching is required for exporting user recordings.

**What Android versions work?** The final supported Android OS and device range must be taken from the signed AAB manifest and real QA results; not yet asserted.

**Can Lite decode NAS/RRC or show Layer 3 messages?** No. It uses documented Android cellular APIs only.

**Can Lite lock LTE bands or cells?** No. It does not perform modem control or require root.

**Can Lite load KML/KMZ/XML cell databases?** No. Lite imports CSV only.

**Why do my signal fields show N/A?** The OS or modem may not provide them; confirm permissions, location settings, SIM and registration state.

**Why is the neighbor list empty?** Android may return zero neighbors or rate-limit cell updates. This is normal for some devices/network states.

**Can I see more than 100 site points?** Lite permits up to 100 unique site points per import selection. Pro editions are planned for larger GIS workflows.

**How many sectors are displayed?** Up to three selected sites may show their genuinely supplied valid sectors; no fake antenna bearing/coverage geometry.

**Why is recording limited to five minutes?** Lite is intended for brief observations. You may save unlimited separate sessions; no daily quota is planned.

**Will it use my data for speed testing?** Yes, user-initiated download/upload tests can use significant mobile data. The test provider and any data sharing must be disclosed before consent.

**Is it available from an APK download?** Public distribution is planned through Google Play. No official public APK download link is available yet.

**Where do I contact support?** The verified public support address/contact mechanism will be provided on https://rfex.app/drive/lite/support/ before launch. No placeholder email address should be published.

## Why are Band Lock, Cell Lock and Signaling visible in Lite?

Lite preserves the Build 98 engineering interface. Band/Cell screens provide actual publicly available read-only radio information, with advanced lock actions shown as inactive, clearly labeled future-edition previews. Signaling provides genuine Android Network Events, **not** raw RRC/NAS messages. The privileged drivers and decoder code are not shipped in Lite.

## Indoor Walk — Lite v1.0.0 (implementation-dependent draft)

Indoor Walk reuses the Build 98 floorplan screen. In Lite, import **one PNG/JPEG floorplan** per session, manually tap survey points while real Android-public-API cell measurements are available, and record for up to **3 minutes of active recording time**. You may start additional separately saved sessions without a daily session count. Export genuine recorded points as **CSV**. Tap positions are relative floorplan image positions, **not GPS positions or calibrated surveyed distances**. Multilevel floorplan workflows, georeferencing/advanced calibration and professional reports are Pro/Advanced feature previews only. No ads while walking or exporting. **Draft: publish only after the Lite build and physical-device QA verify the workflow.**

## Local review build

The candidate uses Android SDK 26 minimum and targets API 36. The Build 98 RF Grid, Strip Chart, Map, settings, recording header and offline Help remain in the app. Band/Cell shows Android observations with radio controls disabled. Network Events & Signaling shows Android cell, service and display observations with a disabled Advanced Pro signaling preview. Indoor Walk accepts one PNG or JPEG per active survey, with three active minutes and CSV coordinates relative to the image. Outdoor sessions use five active minutes. Map tiles are off until enabled in the basemap controls.

## Speed Test providers

OpenSpeedTest Public is the hosted speed test in the release build. Cloudflare Speedtest remains QA-only pending confirmation of hosted-service terms. LibreSpeed is deferred.

Select Open Speed Test, read the disclosure, and select Start in the provider widget. OpenSpeedTest receives your IP address and test traffic. Results stay in its widget.
