# RFeX Drive Lite — Official User Manual

**Document ID:** `RFEX-LITE-UM-001`  
**Product:** RFeX Drive Lite v1.0.0  
**Package:** `com.rfex.drive.lite`  
**Release Date:** November 17, 2026  
**Status:** **Approved Production Manual** (Verified on Xiaomi 13 Pro / Android 13)

---

## 1. Introduction

RFeX Drive Lite is an on-device RF field test instrument engineered for telecom professionals, drive-test technicians, and wireless network enthusiasts. Operating strictly through standard Android public SDK APIs (`TelephonyManager`, `SubscriptionManager`, `LocationManager`), RFeX Drive Lite monitors live 5G NR, 4G LTE, 3G WCDMA, and 2G GSM cellular telemetry without requiring root privileges, kernel patches, or diagnostic daemons.

---

## 2. First-Launch Onboarding & Permissions

When launching RFeX Drive Lite for the first time, a 5-step permission wizard provides complete transparency before requesting system permissions:

1. **Step 1 — Welcome & Architecture:** Explains the 100% public Android SDK architecture and on-device privacy guarantee.
2. **Step 2 — Precise Location (`ACCESS_FINE_LOCATION`):** Required to associate RF measurements with GPS coordinates and render drive-test map trails.
3. **Step 3 — Phone State (`READ_PHONE_STATE`):** Required by Android to read carrier PLMN, SIM slot subscriptions, and cell identity parameters. Clarifies that the app *never* makes or monitors phone calls.
4. **Step 4 — Foreground Notifications (`POST_NOTIFICATIONS`):** Required on Android 13+ to display the persistent notification while a drive-test recording is active in the background.
5. **Step 5 — Diagnostic Checklist:** Displays a summary of granted permissions. Tap `LAUNCH INSTRUMENTS` to enter the main dashboard.

---

## 3. Real-Time RF Telemetry Dashboard

The **RF Status** dashboard provides instantaneous readouts of your serving cellular connection:

- **Primary Serving Carrier:** Operator name (e.g. `SIM1 • Viettel`), MCC/MNC (`452/04`), Registration Status (`Registered`), Mobile Data state.
- **Serving Cell Identity:** 3GPP Band (`LTE B1`), Downlink Frequency (`2135.000 MHz`), Bandwidth (`20.000 MHz`), EARFCN (`250`), Physical Cell ID (`PCI 485`), Tracking Area Code (`TAC 25162`), E-UTRAN Cell Identifier (`ECI 128011273`), Subcarrier Spacing (`15 kHz SCS`).
- **Signal Quality Metrics:**
  - **RSRP:** Reference Signal Received Power in dBm (e.g. `-92.0 dBm`). Color-coded from Green (≥ -85) to Coral (< -105).
  - **RSRQ:** Reference Signal Received Quality in dB (e.g. `-5.0 dB`).
  - **SINR:** Signal to Interference plus Noise Ratio in dB (e.g. `+15.0 dB`).
  - **Timing Advance (TA):** Displayed when in RRC Connected mode; cleanly displays `N/A · not reported by modem (RRC Connected required)` during RRC Idle.
- **Carrier Aggregation (CA):** Displays primary component carrier (PCC) and secondary component carriers (SCC) reported by the Android RIL.
- **Neighbor Cells List:** Live intra-frequency and inter-frequency neighbor cells reported by the modem. Sort dynamically by `RSRP ↓`, `PCI ↑`, or `ARFCN ↑`, or filter by `ALL` vs `INTRA`.

---

## 4. Oscillogram Strip Chart & Correlation

Navigate to the sub-views on the RF Status tab:
- **RF GRID:** Numerical telemetry cards and neighbor cell table.
- **STRIP CHART:** 60-second real-time scrolling oscillogram tracking RSRP fluctuations over time.
- **CORRELATION:** Live scatter plot analyzing signal relationships. In stationary desk conditions (variance = 0), measurement points render unconditionally across the grid with a dashed mean line and display `r = 0.00 (Stationary, n=60)`. Moving in a vehicle or walking immediately displays a linear trendline with Pearson `r`.
- **PARAMS Tab:** Comprehensive hardware diagnostics displaying raw telephony parameters, dual-SIM slot states, and a clean, deduplicated baseband firmware version (`MPSS.DE...`).

---

## 5. Engineering Basemaps & Drive Testing

The **Map** tab provides interactive geographic visualization:

- **Keyless Basemaps:** Tap the Layers button to switch between:
  - **OpenStreetMap Standard (Default):** Crisp worldwide street cartography.
  - **Humanitarian Roads (OSM France):** High-contrast road cartography.
  - **Esri World Imagery:** True top-down high-resolution satellite photography down to rooftop level (Zoom 0–19).
  - **OpenTopoMap:** Elevation contours and topographic relief.
  - **Off / Grid:** Blank coordinate canvas for disconnected or low-resource operation.
- **Cell Site Database & Sector Wedges:**
  - Import custom site lists via CSV (up to 100 sites).
  - Or tap `[ LOAD SAMPLE SITES (3 SITES) ]` in the `CELL DB` dialog to instantly load 3 realistic local LTE sites centered on your current GPS location matching your serving and neighbor PCIs.
  - View 150m illustrative 3GPP antenna azimuth wedges, beamwidths, and serving line-of-sight spider links (`LINKS: ON`).
- **Drive Test Recording:**
  1. Tap `START REC ▾` and select `Outdoor route` or `Outdoor stationary`.
  2. The recording timer and live sample counter will begin logging.
  3. Tap `Stop` when the survey is complete (up to 5 active minutes per session in Lite).
  4. View completed surveys in the **Saved Sessions Manager** (top header Folder icon).
  5. Tap `EXPORT` to save standard CSV logs via the Android Storage Access Framework (SAF).

---

## 6. Indoor Floor Plan Sketch Studio & Walk Testing

The **Indoor** tab enables facility surveys even when architectural CAD files are unavailable:

1. **Draft Sketch Studio:**
   - Tap `DRAFT SKETCH` to open the navy blueprint canvas (`#0B1324`).
   - Draw custom walls, corridors, rooms, and doors, or tap `[ TEMPLATES ]` to load instant architectural presets (`Central Corridor & 4 Offices`, `Warehouse`, or `Multi-Zone Office Grid`).
   - The title block displays clean engineering typography (`RFeX DRIVE LITE - DRAFT FLOOR PLAN`).
   - Tap `USE AS FLOORPLAN` to apply the drawing to the survey canvas.
2. **Conducting the Walk Test:**
   - Tap `START WALK`.
   - Walk your survey route and tap your position on the floorplan canvas.
   - Tap `Pin live RF` to drop numbered pinpoints (1, 2, 3...) color-coded by live RSRP with a dashed walk path.
   - Monitor the on-canvas **Indoor RSRP Legend** (`≥-75` Green, `-85` Lime, `-95` Amber, `<-95` Coral) at the bottom-left of the floorplan.
3. **Undo & Clear Points:**
   - Tap `Undo pin` to remove the last dropped pinpoint.
   - Tap `Clear` to open the confirmation dialog (`Clear All Pinpoints?`) and safely reset survey points to 0 while preserving the active floorplan.
4. **Export Indoor Survey:**
   - Tap `STOP & SAVE` -> tap `Export CSV` to save normalized coordinate logs `(Timestamp, X_Norm, Y_Norm, RAT, PCI, RSRP, RSRQ, SINR)` via Android SAF.

---

## 7. Offline Help & Knowledge Center

Tap the `?` icon in the top header to access the 8-category offline manual:
- **User Manual:** Core instruments and workflows.
- **Drive & Indoor Testing:** Field testing methodologies and coordinate systems.
- **RF Metrics Guide:** 3GPP definitions, ranges, and color thresholds.
- **Permissions & Privacy:** 100% On-Device Privacy Guarantee details.
- **Terms & Compliance:** Freeware license terms and Google Play compliance.
- **Troubleshooting:** Solutions for common modem and GPS quirks.
- **About RFeX:** Built by RF engineering enthusiasts at RFeX Technology.
- **Third-Party Notices:** Complete embedded open-source licenses.
