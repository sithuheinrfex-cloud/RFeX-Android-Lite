# RFeX Drive Lite Changelog

All notable changes to the RFeX Drive Lite application are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.0.0] - 2026-11-16 (Build Code 1)

### Added
- Professional RF engineering dashboard derived directly from RFeX Drive Build 98 QA architecture.
- Real-time serving and neighbor cellular measurement engine utilizing Android public `TelephonyManager` APIs.
- 100% Free, keyless multi-basemap support in osmdroid (Zoom 0–19):
  - OpenStreetMap standard raster tile layer (default, policy-compliant, Zoom 0–19).
  - OpenStreetMap Humanitarian road cartography (hosted by OSM France, Zoom 0–19).
  - Esri World Imagery high-resolution top-down satellite layer (Zoom 0–19).
  - OpenTopoMap topographic relief and terrain contours (Zoom 0–17).
  - Blank grid canvas mode for zero-network operation.
- In-app Basemap selection dialog with real-time layer switching.
- RF measurement point rendering with customizable metric thresholds and engineering legends (RSRP, RSRQ, SINR).
- Outdoor stationary and route drive test session recording (5-minute maximum per session) with CSV export.
- Indoor Walk survey mode with floorplan import (PNG/JPEG) and manual survey point tagging (3-minute maximum per session) with CSV export.
- Cell site CSV import module supporting up to 100 site records and 3-sector azimuth/beamwidth wedges.
- Integrated OpenSpeedTest public web test module with explicit pre-test network disclosure dialog.
- Built-in RFeX Help & Knowledge Center with offline field engineering manuals and third-party notices viewer.

### Changed
- Replaced unauthorized Google Maps raster tile scraping (`mt0.google.com/vt/lyrs=y,m,p`), CARTO hosted dependencies, and low-resolution NASA overview with 100% free, keyless, high-resolution OpenStreetMap Standard, Esri World Imagery (Zoom 0–19), and OpenTopoMap (Zoom 0–17).
- Reconciled `assets/third_party_notices.txt` with current runtime dependencies: removed unused `@cloudflare/speedtest`, CARTO, and NASA notices; added OpenStreetMap France, Esri World Imagery, and OpenTopoMap attributions.
- Set default basemap to policy-compliant OpenStreetMap Standard.

### Removed
- Removed CARTO Dark Matter and Voyager tile providers, `basemaps.cartocdn.com` requests, and all CARTO accounts/keys.
- Removed tracked Python bytecode (`rfex_diag.cpython-312.pyc`) from Git repository.
- Purged all hardcoded Google tile scraping URLs and artificial 7-day Cache-Control HTTP interceptors.
- Removed proprietary modem access, Qualcomm DIAG/QMDL protocols, baseband locking controls, and root-level commands from Lite distribution.

### Fixed
- Fixed map loading failure on restricted/sinkholed local networks by providing keyless OSM fallback mechanisms and documenting private DNS / mobile data routing.
- Verified GNSS satellite position acquisition and location puck synchronization on Android 14 (Xiaomi 13 Pro).
- Fixed runtime `POST_NOTIFICATIONS` permission prompt ordering before initiating foreground recording services.
