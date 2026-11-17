# Known Limitations & Public Android API Boundaries

**Product:** RFeX Drive Lite v1.0.0  
**Package:** `com.rfex.drive.lite`  
**Edition:** Free Edition (Public Android SDK Only)

---

## 1. Architectural Distinctions: Lite vs Advanced Pro

RFeX Drive Lite is intentionally engineered as a zero-root, privacy-first, store-compliant application using public Android SDK APIs. Consequently, certain low-level diagnostic operations are not supported in Lite:

| Feature / Metric | Lite Edition (Public Android API) | Advanced Pro / QA (Root / DIAG Interface) |
| :--- | :--- | :--- |
| **Root Privileges** | Not Required | Required for low-level modem access |
| **Qualcomm DIAG / QMDL** | Excluded (Pure Android HAL) | Supported (Raw protocol layer logging) |
| **Layer 3 Signaling (RRC/NAS)**| Disabled | Decoded PCAP / signaling logs |
| **Band & Cell Locking** | Preview Only (Non-operational) | Active carrier & channel locking |
| **Physical Layer Modulation** | Informational / N/A | Real-time QPSK/16QAM/64QAM/256QAM demodulation |
| **MIMO Layer Rank (RI)** | Public API / N/A | True baseband rank indication |
| **Recording Session Duration** | 5 active minutes (Outdoor) / 3 min (Indoor)| Unlimited continuous multi-hour logging |
| **Cell Database Capacity** | Up to 100 site records | 100,000+ site records with regional filtering |

---

## 2. Telephony & Modem Observations

1. **RRC Idle State TA:** Timing Advance is marked `N/A · not reported by modem (RRC Connected required)` when no active data transfer is occurring. This is standard 3GPP and Android SDK behavior, not an application defect.
2. **Qualcomm Dual-SIM Radio Version:** Devices running dual-SIM modems (e.g. Xiaomi 13 Pro) return comma-separated duplicate radio version strings from `Build.getRadioVersion()`. Lite automatically deduplicates this string into a clean single modem release tag.
3. **Neighbor Cell Reporting Rates:** Android OS throttles background neighbor cell polling to conserve battery. Foreground telemetry refresh intervals (250ms, 500ms, 1s, 2s, 5s) operate at maximum speed permitted by the host OS hardware abstraction layer.

---

## 3. Mapping & Geographic Boundaries

1. **Internet Connectivity for Map Tiles:** OpenStreetMap, Humanitarian, Esri Satellite, and OpenTopoMap basemaps require an active internet connection to download new tile areas. Once downloaded, tiles are cached to local storage.
2. **Offline Fallback:** When internet connectivity is unavailable, select the `Off / Grid` basemap to conduct field surveys over a clean engineering coordinate grid without network delays.
