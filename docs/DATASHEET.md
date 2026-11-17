# RFeX Drive Lite — Technical Datasheet

**Document ID:** `RFEX-LITE-DS-001`  
**Edition:** v1.0.0 Production Release  
**Status:** **Approved Technical Specification** (Verified on Xiaomi 13 Pro / Android 13)  
**Date:** November 17, 2026

---

## 1. Product Identification & Platform Specifications

| Field | Technical Value | Verification Evidence |
| :--- | :--- | :--- |
| **Product Name** | RFeX Drive Lite | Manifest & Build Configuration |
| **Product Family** | RFeX Drive — Mobile RF Engineering Platform | `rfex.app` / `rfex.cloud` |
| **Application ID** | `com.rfex.drive.lite` | Verified across manifest, AAB, and APK |
| **Version Name / Code**| `1.0.0` (Version Code: `1`) | Production release baseline |
| **License** | Proprietary Freeware (Closed source) | 100% Free, Zero Ads, Zero Subscriptions |
| **Target SDK** | API 36 (Android 16 Vanilla Ice Cream) | Fully compliant with Google Play target API rules |
| **Minimum SDK** | API 26 (Android 8.0 Oreo) | Full legacy API backward compatibility |
| **Modem Data Path** | 100% Android SDK Public APIs (`TelephonyManager`) | Zero Root, Zero Qualcomm DIAG, Zero Shannon |
| **Binary Footprint** | Standalone APK: 4.60 MB / Play AAB: 8.84 MB | Pure ART/Dalvik Dex, Zero Native `.so` files |

---

## 2. Technical Capabilities & Measurement Pipeline

### Cellular RF Measurements (Public Android SDK)
Operates through Android `TelephonyManager`, `SubscriptionManager`, `ConnectivityManager`, and `CellInfo` APIs. When metrics are not reported by the host modem, Lite cleanly displays `N/A · not reported by modem (RRC Connected required)` without inventing sentinel zeros.

| RAT | Measurable Parameters | Provenance / Conditions |
| :--- | :--- | :--- |
| **5G NR** | SS-RSRP, SS-RSRQ, SS-SINR, CSI-RSRP, CSI-RSRQ, CSI-SINR, NR-ARFCN, PCI, NCI, TAC | 5G Standalone (SA) & NSA EN-DC anchor observation |
| **4G LTE** | RSRP, RSRQ, RSSI, SINR, Timing Advance (TA), CQI, EARFCN, Band, PCI, TAC, ECI, Bandwidth | Dynamic intra/inter-frequency neighbor tracking |
| **3G WCDMA**| RSCP, Ec/No, UARFCN, Primary Scrambling Code (PSC), LAC, CID | Legacy UMTS cellular observation |
| **2G GSM** | RxLev, RxQual, ARFCN, BSIC, LAC, CID | Legacy 2G cellular observation |

---

## 3. Basemaps, Geographic Engine & Cell Database

- **Mapping Engine:** osmdroid `6.1.18` with custom HTTP disk caching and User-Agent identification (`RFeX-Drive-Lite/1.0.0`).
- **Basemap Providers (100% Free & Keyless, Zoom 0–19):**
  - OpenStreetMap Standard (ODbL, worldwide street cartography)
  - Humanitarian OSM (High-contrast road network)
  - Esri World Imagery (Top-down aerial satellite photography down to rooftop level)
  - OpenTopoMap (Topographic relief with elevation contours)
  - Off / Grid (Offline engineering coordinate grid fallback)
- **Cell Site Management:**
  - Import CSV site files up to **100 unique site locations**.
  - One-tap `[ LOAD SAMPLE SITES (3 SITES) ]` instant demo generator.
  - Directional 3GPP antenna wedges rendered based on CSV azimuth and beamwidth.
  - Serving and neighbor line-of-sight spider links (`LINKS: ON`).

---

## 4. Indoor Blueprint Sketch Studio & Walk Testing

- **Drafting Canvas:** 1200x1200px architectural blueprint grid (`#0B1324`).
- **Drawing Tools:** Walls, rooms, corridors, and doors with multi-color palette.
- **Architectural Templates:** `Central Corridor & 4 Offices`, `Warehouse`, `Office Grid`.
- **Title Block:** Clean ASCII typography (`RFeX DRIVE LITE - DRAFT FLOOR PLAN`).
- **Survey Cadence:** Up to 3 active minutes per indoor walk test session.
- **Pinpoint Tracking:** Normalized coordinate system `(X_Norm, Y_Norm)`.
- **On-Canvas Legend:** Compact **Indoor RSRP Legend** (`≥-75` Green, `-85` Lime, `-95` Amber, `<-95` Coral).
- **Survey Actions:** `Pin live RF`, `Undo pin`, and `Clear` (with safety confirmation dialog).

---

## 5. Session Logging & Storage Access Framework

- **Outdoor Drive Test Recording:** Up to 5 active minutes per session with live sample counter.
- **Saved Sessions Manager:** Horizontal card layout (`20 pts • 1.0 KB`).
- **Export Engine:** Android Storage Access Framework (SAF) standard CSV export. Zero broad storage permissions (`WRITE_EXTERNAL_STORAGE` not requested).
- **Privacy Assurance:** 100% On-Device execution. Zero tracking beacons, zero analytics SDKs, zero background data exfiltration.
