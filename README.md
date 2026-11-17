# RFeX Drive Lite v1.0.0

**Professional Cellular & RF Drive Test Engineering Application for Android**  
*Public Android SDK Architecture — Free Edition*

---

## 1. Application Identification & Specifications

| Property | Value |
|---|---|
| **Application Name** | RFeX Drive Lite |
| **Package / Application ID** | `com.rfex.drive.lite` |
| **Version Name** | `1.0.0` |
| **Version Code** | `1` |
| **Minimum SDK** | `26` (Android 8.0 Oreo) |
| **Target SDK** | `36` (Android 16 Ready / Android 14+ Compliant) |
| **Compile SDK** | `36` |
| **Architecture Foundation** | RFeX Drive Build 98 QA FULL UI & Measurement Pipeline |
| **Runtime Engine** | 100% Android SDK Public APIs (Pure Kotlin/Java, Zero Native C/C++ `.so`, Zero Python) |
| **Release Candidate Directory** | `D:\RFeX-Research\RFeX-Drive-Lite\Release-Candidate\RFeX_Drive_Lite_v1.0.0\Final-Public-Release\` |

---

## 2. Architecture & Compliance Overview

RFeX Drive Lite v1.0.0 delivers professional-grade RF field survey and diagnostic capabilities built directly upon the battle-tested **RFeX Drive Build 98 QA** UI and telemetry foundation. 

### Key Design Tenets:
1. **100% Documented Android Public APIs:** Operates strictly through `TelephonyManager`, `ConnectivityManager`, `SubscriptionManager`, and standard Android `LocationManager` / Fused Location providers. No root access, no Qualcomm DIAG/QMDL interfaces, no modem baseband hooks, and no proprietary vendor binary blobs.
2. **100% Free, Keyless, Policy-Compliant Mapping:** Employs osmdroid with fully authorized, public-compliant, keyless raster basemaps:
   - **OpenStreetMap Standard (Default):** Official worldwide cartography adhering to OSM Tile Usage Policy (ODbL / OpenStreetMap contributors, Zoom 0–19).
   - **Humanitarian OpenStreetMap:** High-contrast street and road cartography hosted by OSM France (Zoom 0–19).
   - **Esri World Imagery:** High-resolution top-down aerial satellite photography down to street/rooftop level (Zoom 0–19).
   - **OpenTopoMap:** Topographic relief with elevation contours and rural roads (Zoom 0–17).
   - **Off / Grid:** Blank canvas with scale markings for offline or privacy-sensitive operations.
   - *Zero Proprietary Services:* 100% keyless; zero dependence on CARTO accounts, API keys, or billing quotas. All direct scraping of Google Maps raster tiles (`mt0.google.com`) has been completely eradicated.
3. **Clean Runtime Footprint:** No residual diagnostic bytecode, no Chaquopy/Python interpreters, no native C/C++ binaries. Total release APK size is ~4.58 MB.

---

## 3. Lite Edition Scope & Guardrails

| Module | Feature Scope | Lite Enforcement / Guardrails |
|---|---|---|
| **RF Status & Dashboard** | Serving cell, neighbor cells, 2G/3G/4G/5G parameters (RSRP, RSRQ, RSSI, SINR, CQI, TA, PCI, TAC, EARFCN, NR-ARFCN) | Real-time observation via public APIs. Unavailable hardware values cleanly marked `N/A`. |
| **RF Engineering Map** | Live GPS/GNSS puck, route breadcrumbs, RF measurement points color-coded by RSRP/RSRQ/SINR with dynamic engineering legend | Fully active with OpenStreetMap Standard, Humanitarian OSM, Esri Satellite, OpenTopoMap, or Grid basemaps. |
| **Cell Site Database** | CSV site database loading, tower icons, serving site line-of-sight vector | Up to **100 distinct site records** loaded per session. |
| **Sector Visualization** | Directional antenna wedge rendering based on azimuth and beamwidth | Up to **3 selected cell sites** visualized simultaneously. |
| **Drive Test Recording** | Outdoor stationary & drive survey recording to CSV format | **5 minutes active recording** per session. Unlimited separately saved sessions. |
| **Indoor Walk Survey** | Floorplan canvas, single PNG/JPEG import, manual survey point tagging, CSV export | **3 minutes active recording** per session. 1 imported floorplan per session. |
| **Network Events** | Real-time log of cell handovers, RAT switches, connection state changes | Public Android network events log. Decoded modem protocol signaling disabled. |
| **Connectivity & Speed** | TCP ping latency probes and OpenSpeedTest public web test integration | User-initiated only with explicit modal disclosure. No third-party tracking. |
| **Band & Cell Locking** | Radio state information display | Informational preview only. Modem carrier-locking controls disabled in Lite. |

---

## 4. Release Artifacts & Verification

The final release candidate files are packaged under:  
`D:\RFeX-Research\RFeX-Drive-Lite\Release-Candidate\RFeX_Drive_Lite_v1.0.0\Final-Public-Release\`

- `RFeX_Drive_Lite_v1.0.0_1_unsigned-review.aab` (Android App Bundle for Google Play Console)
- `RFeX_Drive_Lite_v1.0.0_1_unsigned-review.apk` (Standalone APK for manual sideloading / testing)
- `evidence-final-map-carto-dark.png` (Live Xiaomi 13 Pro physical device verification)
- `evidence-final-basemap-dialog.png` (Basemap selection dialog evidence on physical device)
- `evidence-final-third-party-notices.png` (In-app legal notices verification on physical device)
- `THIRD_PARTY_NOTICES.txt` (Comprehensive license & attribution manifest)
- `SBOM.json` (Complete dependency software bill of materials)
- `SHA256SUMS.txt` (Cryptographic verification checksums)

---

## 5. Device Compatibility

- **Target Architecture:** ARM64-v8a, armeabi-v7a, x86_64.
- **Physical Device Verified:** Xiaomi 13 Pro (Model `2210132G`, Snapdragon 8 Gen 2, Android 14 / HyperOS, compile/targetSdk 36).
- **Dual-SIM Support:** Verified with Subscriptions 1 & 2 via Android `SubscriptionManager`.
