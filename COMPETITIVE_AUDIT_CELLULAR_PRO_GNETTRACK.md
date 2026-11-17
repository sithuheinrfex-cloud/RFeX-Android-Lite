# RFeX Drive Lite — Competitive Audit: Cellular Pro & G-NetTrack Lite

**Target Device:** Xiaomi 13 Pro (`2210132G`, Snapdragon 8 Gen 2, Android 14 HyperOS)  
**Date:** November 17, 2026  
**Audited Applications:**
1. **Cellular Pro** (`make.more.r2d2.play.cellular_pro`, v2.0.16, Build 110, targetSdk 36)
2. **G-NetTrack Lite** (`com.gyokovsolutions.gnettracklite`, v20.5, Build 273, targetSdk 36)
3. **RFeX Drive Lite** (`com.rfex.drive.lite`, v1.0.0, Build 1, targetSdk 36)

---

## 1. Application Architecture & Permissions Comparison

| Dimension | Cellular Pro (v2.0.16) | G-NetTrack Lite (v20.5) | RFeX Drive Lite (v1.0.0) |
|---|---|---|---|
| **Package ID** | `make.more.r2d2.play.cellular_pro` | `com.gyokovsolutions.gnettracklite` | `com.rfex.drive.lite` |
| **Target SDK / Min SDK** | `targetSdk 36` / `minSdk 23` | `targetSdk 36` / `minSdk 23` | `targetSdk 36` / `minSdk 26` |
| **Installed APK Size** | 55.8 MB (Split APKs) | 6.57 MB (Single APK) | **4.57 MB (Universal APK)** |
| **Map Rendering Engine** | Mapbox Maps SDK (Vector) | Google Maps Android SDK (v2) | **osmdroid (Multi-Source Raster Engine)** |
| **Basemap Dependency** | Proprietary Mapbox hosted styles | Google Play Services + Google API Key | **100% Free & Keyless (OSM, Esri Satellite, OpenTopoMap, Grid)** |
| **Location Permission** | Fine & Coarse Location | Fine, Coarse, & Background Location | **Fine & Coarse Location** |
| **Foreground Service** | `FOREGROUND_SERVICE_LOCATION` | `FOREGROUND_SERVICE_LOCATION` | **`FOREGROUND_SERVICE_LOCATION`** |
| **Notification Permission** | `POST_NOTIFICATIONS` | `POST_NOTIFICATIONS` | **`POST_NOTIFICATIONS`** |
| **System Alert Window** | Not requested | Requested (`SYSTEM_ALERT_WINDOW`) | **Not requested (Clean Play Policy)** |
| **Root/DIAG Capabilities** | Contains `dcidaemon`, `diag_lte.cfg` for root | None (Public API only) | **Pure Android Public APIs (Zero DIAG/Root)** |

---

## 2. Permission Alignment & Play Store Compliance

Both Cellular Pro and G-NetTrack Lite require two primary runtime permissions on non-rooted Android 14 devices:
1. `android.permission.ACCESS_FINE_LOCATION` (Precise GPS tracking & carrier cell visibility)
2. `android.permission.READ_PHONE_STATE` (TelephonyManager serving cell & signal strength observation)

### Key Observations on Permissions:
* **Background Location (`ACCESS_BACKGROUND_LOCATION`):** G-NetTrack Lite requests background location, which Google Play subjects to strict policy reviews, mandatory video demonstrations of core use cases, and prominent in-app disclosure dialogs.
* **Floating Window (`SYSTEM_ALERT_WINDOW`):** G-NetTrack Lite requests drawing over other apps for a floating widget. On Android 14/15, this triggers extra security scrutiny.
* **RFeX Drive Lite Compliance Advantage:** RFeX Drive Lite uses `FOREGROUND_SERVICE_LOCATION` paired with `POST_NOTIFICATIONS`. When a drive test recording is active, a persistent Android notification informs the user, fulfilling Google Play's location-in-use policy without needing high-risk background location permissions.

---

## 3. Professional Tool Visual & Functional Alignment

Industry-standard cellular survey tools (TEMS Pocket, Cellular Pro, G-NetTrack Pro, Nemo Handy) share a distinct set of professional UI conventions. Here is how RFeX Drive Lite aligns with and enhances them:

### A. Real-Time RF Engineering Dashboard
* **Cellular Pro / G-NetTrack Approach:** Displays serving cell parameters in a dense, dark-themed monospace table: MCC-MNC, TAC, eNB/gNB ID, Cell ID, PCI, EARFCN/ARFCN, Band, Bandwidth, RSRP, RSRQ, RSSI, SINR, CQI, TA.
* **RFeX Drive Lite Enhancement:** Inherited directly from RFeX Drive Build 98 QA:
  - Dual-SIM real-time switching at the header (e.g. `● SIM1 Viettel`, `SIM2 No SIM`).
  - Color-coded KPI thresholds (RSRP: Very Good $\ge -85$, Good $-85$ to $-95$, Fair $-95$ to $-105$, Poor $-105$ to $-115$, Very Poor $< -115$ dBm).
  - Serving cell and neighbor cell ranking with strip chart timeline.

### B. Map & GPS Tracking Display
* **Cellular Pro / G-NetTrack Approach:**
  - 2D top-down view centered on GPS puck.
  - Route breadcrumb dots color-coded by the active KPI (RSRP, RSRQ, SINR).
  - Line-of-sight line from user's location to serving cell tower.
  - Sector antenna wedges (azimuth and beamwidth).
* **RFeX Drive Lite Enhancement:**
  - **5 Keyless Basemaps:** OpenStreetMap Standard, Humanitarian Roads (OSM France), Esri High-Resolution Satellite (Zoom 0–19), OpenTopoMap (Terrain), and Off/Grid.
  - **Interactive KPI Distribution Legend Box:** Floating auto-switching distribution box showing exact sample counts and percentage breakdowns per threshold bin, with customizable colors and hex codes.
  - **Engineering Quick Toggles:** Bottom quick-toggles for `TRAIL: ON/OFF`, `SECTORS: ON/OFF`, `LINKS: ON/OFF`, and `CLR TRAIL`.

### C. Cell Site Database & Sector Visualization
* **G-NetTrack Approach:** Loads `cellfile.txt` (tab-delimited `CELLID, LAC, MCC, MNC, LAT, LON, AZIMUTH, BEAMWIDTH`).
* **RFeX Drive Lite Enhancement:** CSV site database loader supporting up to 100 site locations with 3-sector azimuth/beamwidth geometry, with line-of-sight connecting vectors to the serving cell.

### D. Indoor Floorplan Walk Survey
* **Cellular Pro / G-NetTrack:** Either absent in free versions or requires expensive paid enterprise licenses.
* **RFeX Drive Lite Advantage:** Built-in **Indoor Walk Survey** mode. Allows importing local floorplans (PNG/JPEG), tapping survey points along the walk path, recording 3-minute sessions, and exporting synchronized CSV logs.

---

## 4. Rollout Readiness Conclusion

RFeX Drive Lite v1.0.0 is fully aligned with industry-standard professional RF tools while maintaining:
1. **Zero API Key Dependencies:** Does not require Google Maps or Mapbox developer accounts.
2. **Lean Footprint:** ~4.57 MB universal package vs Cellular Pro's 55.8 MB.
3. **Strict Android Public API Safety:** Zero root/DIAG requirements and zero restricted background permissions.
4. **Verified Physical Hardware Execution:** Tested and operational on Xiaomi 13 Pro running Android 14 HyperOS.
