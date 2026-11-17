# RFeX Drive Lite v1.0.0 Release Notes

**Version Name:** 1.0.0  
**Version Code:** 1  
**Package Name:** `com.rfex.drive.lite`  
**Target SDK:** 36 (Android 16 Ready / Android 14+ Compliant)  
**Minimum SDK:** 26 (Android 8.0 Oreo)  
**Release Date:** November 16, 2026  
**Git Baseline Commit:** `bc09866`  

---

## Highlights

RFeX Drive Lite v1.0.0 is the inaugural public release of the lightweight, privacy-focused cellular radio frequency survey and drive-testing tool. Built upon the production-tested UI foundation of RFeX Drive Build 98 QA, Lite provides cellular engineers, technicians, and enthusiasts with essential field survey capabilities using documented Android SDK public APIs.

### Key Capabilities in v1.0.0
- **Real-Time RF Status:** Instantaneous monitoring of LTE and 5G NR serving and neighbor cells, including RSRP, RSRQ, RSSI, SINR, CQI, Timing Advance, Physical Cell ID (PCI), and ARFCN.
- **Dynamic Keyless Multi-Basemap Support (100% Free & No Accounts, Zoom 0–19):** 
  - **OpenStreetMap Standard (Default):** Worldwide street basemap adhering to the official OSM Tile Usage Policy (ODbL, Zoom 0–19).
  - **Humanitarian Roads (OSM France):** High-contrast road cartography optimized for route tracking (Zoom 0–19).
  - **Satellite Imagery (Esri World Imagery):** True top-down high-resolution aerial satellite imagery down to street/rooftop level (Zoom 0–19), replacing low-resolution NASA Blue Marble.
  - **Topographic Relief (OpenTopoMap):** Elevation contours, shading, and rural road networks (Zoom 0–17).
  - **Off (Grid Fallback):** Minimalist engineering coordinate grid for offline field surveys.
- **Live Survey Recording:** Record 5-minute outdoor drive-test sessions with synchronized GPS coordinates and RF metrics, exported directly to standard CSV format.
- **Indoor Walk Survey:** Import floorplans (PNG/JPEG) and manually tag survey points with 3-minute recording sessions and CSV export.
- **Cell Site Management:** Load up to 100 site locations via CSV, with 3-sector azimuth/beamwidth visualizers and serving site line-of-sight tracking.
- **In-App Knowledge & Compliance:** Offline RF parameter guides, field diagnostic handbook, and transparent third-party open-source attribution notices.

---

## Release Blocker Remediation Summary

Prior to final release candidate packaging, the following release blockers and security audits were formally resolved:

1. **Purged Google Tile Scraping & CARTO Hosted Services (BLOCKER-MAP-01):**
   - Completely eradicated unauthorized `mt0.google.com` tile scraping endpoints.
   - Removed all dependencies on CARTO API keys, accounts, quotas, and `basemaps.cartocdn.com` endpoints.
   - Adopted policy-compliant, 100% keyless OpenStreetMap Standard as the official default basemap, with Humanitarian OSM, Esri World Imagery (Zoom 0–19), and OpenTopoMap options.
   - Configured compliant User-Agent headers and standard HTTP disk caching without artificial header overrides.
2. **Purged Residual DIAG Bytecode (MEDIUM-SEC-01):**
   - Removed tracked Python `.pyc` bytecode (`rfex_diag.cpython-312.pyc`) from Git history and source trees.
   - Updated `.gitignore` to permanently exclude Python compiled artifacts.
3. **Reconciled Third-Party Legal Notices (HIGH-NOTICES-01):**
   - Purged residual `@cloudflare/speedtest` and CARTO references.
   - Preserved OpenStreetMap, NASA Blue Marble, osmdroid, OpenSpeedTest, and AndroidX attributions.
   - Verified live in-app legal notice presentation on physical device.
4. **Android 14/15 Permission Hardening (LOW-NOTIF-01):**
   - Verified that `POST_NOTIFICATIONS` runtime permission is requested transparently prior to starting foreground drive-test recording services.
   - Enforced strict user-facing disclosure prior to accessing location and connectivity services.

---

## Verified Device Target
- **Xiaomi 13 Pro (`2210132G`):** Fully tested and verified under Android 14 (HyperOS, Snapdragon 8 Gen 2). GPS location acquisition, live CARTO Dark basemap rendering, RF measurement trail coloring, and session recording verified end-to-end.
