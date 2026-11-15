# RFeX Drive Lite — User Manual

**Document ID:** RFEX-LITE-UM-001 · **v1.0.0 candidate** · Updated 2026-11-13 · **Draft until actual app UI is tested.**

This guide describes the required Lite workflow. Codex must reconcile screen names and actions with the real compiled v1.0.0 app, then replace any draft-only description with tested steps.

## 1. Introduction

RFeX Drive Lite shows basic serving-cell and available neighbor-cell measurements provided by public Android SDK APIs. It is designed for checking coverage and taking short RF field observations, not for controlling the modem or decoding raw protocol signaling; it can show publicly observed Android network events. Available fields vary by handset and operator.

## 2. Installation

1. Install **RFeX Drive Lite** from its verified Google Play listing when available.
2. Open the app and read the concise privacy and permissions explanations.
3. Choose **Enable Precise Location** and select **Precise** and **While using the app**. Choose **Continue with Limited Features** to skip. Approximate access, Location Services off or a denial can limit cell identity, GNSS and recording.
4. Use **Allow SIM access** separately when supported subscription selection is needed. Lite asks about notifications when starting an outdoor recording on Android 13 or later. `READ_PHONE_STATE` is not a universal requirement for every public cellular metric and should not be requested unnecessarily.
5. You may open the labeled Demo mode to explore the interface without pretending sample readings are live measurements.

**No root, Qualcomm DIAG, USB scanner or special system permission is required.**

## 3. Dashboard

The dashboard should display the detected SIM or data subscription, current RAT (2G/3G/4G/5G), serving cell identification and actual available RF signal values. Tap measurement details to show units and descriptions. Typical examples include LTE RSRP/RSRQ/RSSNR and 5G SS-RSRP/SS-RSRQ/SS-SINR. Values absent from Android are **N/A**. Do not assume a neighbor list must be present at all times. Android limits update frequency; short-lived blank/old cells must be clearly indicated by age/state.

## 4. Dual-SIM and neighbor-cell behavior

When multiple SIMs exist, choose the available subscription context in the app, where Android permits. Some measurements refer to the active/default data SIM; vendor restrictions may prevent full simultaneous readings. Other cells shown by `CellInfo` are OS-reported neighbor/registered records, not a full RF sweep. Permission refusal, airplane mode, SIM removal and roaming should be handled gracefully.

## 5. Live map and RF trail

Open Map, enable current location and choose the available metric/color legend. Confirm the location marker corresponds to an actual GNSS/location fix. Start a recording before relying on a route trail as a saved dataset. Site markers show CSV imported records. Sectors are previews of real sector records, not propagation predictions. Map tiles may require an internet connection and display OpenStreetMap attribution per the chosen provider terms.

## 6. Import CSV site points (Free cap)

1. Prepare a CSV containing a distinct `site_id` and valid decimal `latitude`, `longitude` for each site; see [CSV guide](CSV_SITE_FORMAT.md).
2. In the app open the Site Database/Import CSV feature.
3. Use Android's file picker to select the CSV. A system file picker does not require All Files Access.
4. Review parsed row counts, unique site count and rejected rows before confirming.
5. If more than 100 unique sites exist, select a subset explicitly; the app must not silently truncate.
6. Enable the **Site Points** layer to display up to 100 imported sites.
7. Select up to **3 sites** to enable **Sector Preview**. Sector preview requires valid sector IDs and geometry parameters from the CSV; otherwise show markers only.
8. Toggle Site Points, Sector Preview and RF Trail independently.

**Not supported for Lite import:** `.kml`, `.kmz`, `.xml`, `.tab` and other advanced formats.

## 7. Record a five-minute field session

1. Check permission status, available storage, live RF values and GNSS fix.
2. Open **Test setup**, select an outdoor survey type, then tap **Start recording**. Verify the recording indicator, elapsed recorded time and privacy notification as applicable.
3. Use **Pause/Resume** to temporarily stop/resume acquisition. Confirm the displayed elapsed recorded time excludes pauses.
4. Open the recording controls and tap **Stop and save**. The confirmation shows the start and stop times, active duration, saved CSV name, and storage folder. At **5:00 recorded minutes**, the app must auto-stop, flush buffered genuine samples and save the session.
5. Open Saved Sessions to inspect timestamp, session name, duration, sample count and available metrics.
6. You may start another five-minute session; there is no daily quota.

**No data should be fabricated to fill GNSS gaps or interrupted time periods.**

## 8. Export CSV or GPX

Open Saved Sessions, select one, choose Export and then CSV or GPX. Use Android's document picker to choose where the file goes. Check that CSV fields are well-escaped and timestamps have an explicit timezone/UTC representation. GPX contains actual recorded geographic coordinates only. If there is no valid location, explain why a GPX route may be empty. Avoid exporting private phone numbers, IMSI/ICCID or invented modem counters.

## 9. Connectivity and speed test

Ping/reachability test: press Start; inspect response results, timeouts and any protocol-specific definitions. Do not label HTTP or TCP reachability as ICMP RTT if ICMP wasn't used.

Speed test: review the data-usage and third-party processing notice, decide whether to proceed, then press Start. Results must show only supported genuine measurements. This test uses network data and may affect a mobile data plan. Cancel or server error must result in truthful partial/error state. Exact provider-specific disclosures will be finalized before publication.

## 10. Advertising

Idle-screen ads are displayed unobtrusively, subject to privacy and consent requirements. Ads should never cover measurement controls or run during recording, active tests, map interaction, file import or export. You do not need to watch ads to export your own logs.

## 11. Data and permissions

The app may use location and public cellular data to display live values and save your selected local sessions. Online maps, ad networks and optional network-test services involve external network requests. Review the public privacy policy for confirmed third-party recipients, retention and deletion details once finalized. Permissions can be managed in Android Settings > Apps > RFeX Drive Lite > Permissions. Exact menus vary by OS.

## 12. Troubleshooting

| Symptom | Check / interpretation |
|---|---|
| RF value is N/A | Device/OS/operator may not expose it; confirm location and precise permission if required |
| No neighbor cells | Public Android API may provide none or throttle refresh; this is not necessarily a bug |
| Site file rejected | Ensure CSV UTF-8, unique site IDs, decimal coordinates and valid column headers |
| 100-site limit reached | Select at most 100 unique sites explicitly; do not delete your original file |
| No sectors visible | Select a site with valid azimuth/beamwidth/sector columns; do not infer from site coordinates |
| Recording stops at 5 min | Expected Lite limit; start another session |
| No GPX points | No valid location fix during recording; verify location settings |
| Map blank offline | Online tile provider might require connectivity; offline maps not guaranteed |
| Speed test fails | Network/server unreachable, interrupted test, data restrictions or provider problem |
| Ads don't load | Application should remain functional; advertising is optional to app operation |

## 13. Support and upgrades

Public help: https://rfex.app/drive/lite/support/ (target URL, not live at document creation). Pro, Advanced Pro and Enterprise are future separately distributed products. Do not assume paid packages can read Lite's app-private storage directly; use explicit export/import when supported.

**Important:** The existing Band Lock and Cell Lock *screens* remain useful read-only cellular-information panels, but **actual locks are not available in Lite**. The Signaling screen shows Android public-API network events, **not decoded Layer 3/NAS/RRC protocol messages**. Root/DIAG, PCTEL control, privileged modem operations and certified spectrum measurements are not shipped. RF results are OS-exposed indicators.

## 14. Familiar Band Lock, Cell Lock and Signaling screens in Lite

**Band Lock:** Navigate to the existing screen and inspect the available current band and frequency/channel. Any lock switch/button is an **inactive Pro/Advanced preview**, not an operation. It must never change handset radio settings.

**Cell Lock:** Inspect the genuine observed serving PCI/Cell ID/TAC/channel and available neighbors. A changed PCI or cell is an observation; it does not prove an RRC handover cause. Cell/PCI lock actions are not offered in Lite.

**Signaling:** Open the existing screen to see **Android Network Events**, with timestamps and source. Events can include service state changes, signal measurements, network type changes, data connection changes and detected serving-cell changes. An empty timeline means no event has been received yet. A clearly labeled RRC/NAS protocol pane, if shown, is a future-edition preview only. Lite never decodes modem protocol messages.

These features depend on permissions, Android version, chipset/carrier behavior and real device testing. Never interpret an absent event as proof that no radio-layer event occurred.

## Indoor Walk — Lite v1.0.0 (implementation-dependent draft)

Indoor Walk reuses the Build 98 floorplan screen. In Lite, import **one PNG/JPEG floorplan** per session, manually tap survey points while real Android-public-API cell measurements are available, and record for up to **3 minutes of active recording time**. You may start additional separately saved sessions without a daily session count. Export genuine recorded points as **CSV**. Tap positions are relative floorplan image positions, **not GPS positions or calibrated surveyed distances**. Multilevel floorplan workflows, georeferencing/advanced calibration and professional reports are Pro/Advanced feature previews only. No ads while walking or exporting. **Draft: publish only after the Lite build and physical-device QA verify the workflow.**


## Speed testing — existing Build 98 interface


## Local review build

The candidate uses Android SDK 26 minimum and targets API 36. The Build 98 RF Grid, Strip Chart, Map, settings, recording header and offline Help remain in the app. Band/Cell shows Android observations with radio controls disabled. Network Events & Signaling shows Android cell, service and display observations with a disabled Advanced Pro signaling preview. Indoor Walk accepts one PNG or JPEG per active survey, with three active minutes and CSV coordinates relative to the image. Outdoor sessions use five active minutes. Map tiles are off until enabled in the basemap controls.

## Speed Test providers

OpenSpeedTest Public is the hosted speed test in the release build. Cloudflare Speedtest remains QA-only pending confirmation of hosted-service terms. LibreSpeed is deferred.

Select Open Speed Test, read the disclosure, and select Start in the provider widget. OpenSpeedTest receives your IP address and test traffic. Results stay in its widget.

### Map status and Indoor Walk display

Enable online tiles in the basemap control. If the tile service is unreachable, the map shows an unavailable notice. The RF overlay uses location-tagged samples and the selected metric when the device reported it. An empty RF or cell database message indicates that no matching points or sites are loaded.

Indoor Walk fits PNG or JPEG floorplans to the canvas while preserving their proportions. Tap within the image to place a relative measurement point while recording. Manual connectivity and hosted speed tests remain in Lite. Manual call/SMS launchers, sketch tools, crop/rotate/straighten and distance calibration are deferred.
