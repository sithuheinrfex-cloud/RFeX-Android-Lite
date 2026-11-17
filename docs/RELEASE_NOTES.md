# RFeX Drive Lite v1.0.0 Release Notes

**Version Name:** 1.0.0  
**Version Code:** 1  
**Package ID:** `com.rfex.drive.lite`  
**Target SDK:** 36 (Android 16 Ready / Android 14+ Compliant)  
**Minimum SDK:** 26 (Android 8.0 Oreo)  
**Release Date:** November 17, 2026  
**Git Source Commit:** `a0b7bd6` (Branch: `review/lite-v1.0.0-build98`)

---

## Highlights

RFeX Drive Lite v1.0.0 is the inaugural production release of the lightweight, privacy-focused cellular radio frequency survey and drive-testing tool. Built upon the production-tested UI foundation of RFeX Drive Build 98 QA, Lite provides cellular engineers, technicians, and enthusiasts with essential field survey capabilities using documented Android SDK public APIs.

### Key Capabilities in v1.0.0

- **Real-Time Cellular Radio Telemetry:** Instantaneous monitoring of LTE and 5G NR serving and neighbor cells, including RSRP, RSRQ, RSSI, SINR, CQI, Timing Advance, Physical Cell ID (PCI), and ARFCN.
- **Keyless Multi-Basemap Engine (100% Free, No Accounts, Zoom 0–19):**
  - **OpenStreetMap Standard (Default):** Worldwide street map adhering to the official OSM Tile Usage Policy (ODbL).
  - **Humanitarian Roads (OSM France):** High-contrast road cartography optimized for route surveys.
  - **Satellite Imagery (Esri World Imagery):** True top-down high-resolution aerial satellite imagery down to rooftop level.
  - **Topographic Relief (OpenTopoMap):** Elevation contours, shading, and rural road networks.
  - **Offline Grid:** Minimalist engineering coordinate grid for offline or low-resource field surveys.
- **Serving & Neighbor Cell Visualization:** 1-tap `[ LOAD SAMPLE SITES (3 SITES) ]` or import custom cell files via CSV (up to 100 sites) to display 3GPP antenna azimuth wedges, beamwidths, and live serving/neighbor line-of-sight spider links (`LINKS: ON`).
- **Indoor Floor Plan Sketch Studio & Walk Testing:**
  - On-device blueprint drafting studio with architectural templates (`Central Corridor & 4 Offices`, `Warehouse`, `Office Grid`) or freehand wall/room drawing.
  - On-canvas **Indoor RSRP Legend** (`≥-75`, `-85`, `-95`, `<-95`).
  - Drop live RF pinpoints, view color-coded walk test trails, undo pins, or clear survey points with confirmation dialog.
- **Drive Test Sessions & Export:** Continuous outdoor route logging with synchronized GPS, Android SAF CSV export, and horizontal Saved Sessions Manager (`20 pts • 1.0 KB`).
- **Offline Help & 3GPP Knowledge Base:** 8-category in-depth manual including User Manual, Drive & Indoor Testing, RF Metrics Guide, Permissions & Privacy, Terms & Compliance, Troubleshooting, About RFeX, and Third-Party Open Source Notices.
- **100% On-Device Privacy Guarantee:** Zero tracking beacons, zero analytics SDKs, zero background data exfiltration, and zero advertising libraries.

---

## Release Artifacts & SHA-256 Checksums

- **Google Play Bundle:** `RFeX_Drive_Lite_v1.0.0_1_release_signed.aab`  
  `7fb4a28c0bc3618f4705157fea691da773e2b2e9545be49ee78e456bd3d296ed`
- **Sideload APK:** `RFeX_Drive_Lite_v1.0.0_1_release_signed.apk`  
  `7dce308c8d4894bc39bd3c6bdb32d37bab25d5db60ad9f1c417e70ffe9325542`

*Signed with official release keystore (`rfex-release-key`) verifying v1, v2, and v3 Android signature schemes.*
