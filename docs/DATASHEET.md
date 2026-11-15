# RFeX Drive Lite — Technical Datasheet

**Document ID:** RFEX-LITE-DS-001 · **Edition:** v1.0.0 candidate · **Status:** Proposed specification; hardware/support claims require release QA · **Date:** 2026-11-13

## 1. Product identification

| Field | Value |
|---|---|
| Product | RFeX Drive Lite |
| Family | RFeX Drive — Drive Test Platform |
| Platform | Android, with Kotlin/Jetpack Compose planned |
| Package ID | `com.rfex.drive.lite` (verify with Play Console before first upload) |
| Version | `1.0.0` (`versionCode=1` if unused) |
| Commercial edition | Free to install; ads are declared and disclosed |
| Modem data path | Documented Android SDK APIs only |
| Root, DIAG, privileged permissions | Not required or shipped |
| Release signing / supported OS range | Must be populated from final signed AAB and device test report |
| Internet use | Online maps, advertising and optional network tests require connectivity |

## 2. Technical capabilities and boundaries

### Cellular measurements

Uses public documented APIs, e.g. `TelephonyManager`, `TelephonyCallback`, `CellInfo`, `CellIdentity*`, `CellSignalStrength*`, `SubscriptionManager` as allowed, plus `ConnectivityManager` for current data connectivity. The phone may restrict readings by hardware, carrier, OS, location permission, and throttling. Never report unavailable values as `0`, fabricated values or measured values. Show **N/A** and provenance when appropriate.

| RAT | Typical public-API observations — only where actually returned |
|---|---|
| GSM / 2G | Registration, MCC/MNC, LAC/CID, ARFCN/BSIC and signal strength where exposed |
| WCDMA / 3G | Cell identity, UARFCN/PSC and signal strength where exposed |
| LTE / 4G | Serving/neighbor registration, EARFCN/band, PCI, TAC/CI, RSRP, RSRQ, RSSNR/SINR where exposed |
| NR / 5G | NR-registered cell identity and SS-RSRP/SS-RSRQ/SS-SINR only where exposed; NSA devices may omit individual fields |

**UI distinction:** Lite retains Build 98 Band Lock and Cell Lock screens as **read-only cellular information + disabled Pro/Advanced lock previews**. It retains the Signaling screen as a **real public-API Android Network Events** timeline (state/signal/observed serving-cell changes). **Not included:** raw RRC/NAS protocol decoding/capture, signaling causes or layer-3 PDUs, spectrum scans, vendor modem bridges, actual lock execution, or scanner drivers. The app cannot guarantee all metrics/events on all devices.

### Map and GNSS

Uses standard Android location APIs for user-consented location. Includes visible site points, a selected live RF trail and color legend. Offline coverage or map-tile rights are **not** claimed unless separately implemented/validated. No sector geometry shall be invented from a single site point.

### CSV site database

- Input: `.csv` only via Android Storage Access Framework.
- Maximum: **100 unique site IDs/site locations**, with deduplication of multiple sector records.
- Sectors: show **all valid sector records for up to 3 user-selected sites**, within documented renderer safety limits. Missing azimuth/beamwidth means site marker only.
- Reject unsupported KML/KMZ/XML/TAB/MIF formats with a helpful message; do not silently import or misread XML.
- Input stays unmodified; no file-system-wide storage permission.

### Recording and export

- Up to **5 minutes of actual recorded time per session**; paused intervals do not count toward the cap.
- Unlimited separately initiated sessions; auto-stop, flush and save when the cap is reached.
- Export completed recordings to **CSV and GPX**, with real timestamp, selected SIM/network, available RF values and GNSS location where captured. Unavailable values remain blank/N/A.
- Export only after explicit user action; no required ad view or account registration.

### Basic connectivity tests

- User-initiated ping: bounded packet count and timeouts. Identify TCP/HTTP reachability separately from true ICMP if protocol restrictions require it.
- User-initiated one-shot speed test: DL/UL throughput and supported latency details only when actually measured. Warn about mobile data usage and any third-party processing. No silent auto-test or invented packet loss/jitter.

### Advertising and privacy

- AdMob banner/native placement limited to idle dashboard/help/saved sessions; not over active measurement, recording, map interaction, import/export or test controls.
- Privacy-consent/UMP flow where applicable; full SDK data inventory and Google Play Data safety alignment required.
- No forced sign-in. User-generated local session deletion/export controls.

## 3. Performance and compatibility disclaimers

Measurement update rate is constrained by Android/device and is **not guaranteed**. GNSS accuracy is estimated by Android and dependent on environment; this is not calibrated survey equipment. App-reported cellular values are diagnostic indicators, not regulator-certified measurements. Speed-test results depend on server, radio load, local routing and data plan; no guaranteed throughput or target latency.

## 4. Required release evidence

Before removing 'candidate' from this datasheet, attach source revision, final merged manifest, dependency/SBOM license audit, signed bundle identity and SHA256, clean installs, per-RAT real-device screenshots, CSV 100/101 site tests, 3-site sector preview tests, five-minute recorder auto-stop tests, exports, ad/privacy checks and link verification. List any unsupported devices or test gaps.

## 5. Intended upgrade path

Future **Pro**, **Advanced Pro** and **Enterprise** are separate apps, labeled **Coming soon** in Lite until real listings exist. Lite does not contain disabled privileged engineering binaries. Data transfer to future editions, if added, must use user-initiated export/import.

## 6. Retained Build 98 engineering navigation (Lite preview mode)

| Screen | Lite functional surface | Paid-only preview |
|---|---|---|
| Band Lock | Read actual publicly reported LTE/NR band, channel and RAT | Modem band lock is disabled, not emulated |
| Cell Lock | Read actual serving/available neighbor PCI, cell ID and ARFCN | Cell/PCI lock is disabled, not emulated |
| Signaling | Timestamped TelephonyCallback/service/cell events, with source and N/A | RRC/NAS raw protocol decoding shown as unavailable |

These are **planned/release-candidate** surfaces until verified on the Lite APK. No Pro/Advanced locking or decoded signaling is guaranteed for future unsupported hardware.

## Indoor Walk — Lite v1.0.0 (implementation-dependent draft)

Indoor Walk reuses the Build 98 floorplan screen. In Lite, import **one PNG/JPEG floorplan** per session, manually tap survey points while real Android-public-API cell measurements are available, and record for up to **3 minutes of active recording time**. You may start additional separately saved sessions without a daily session count. Export genuine recorded points as **CSV**. Tap positions are relative floorplan image positions, **not GPS positions or calibrated surveyed distances**. Multilevel floorplan workflows, georeferencing/advanced calibration and professional reports are Pro/Advanced feature previews only. No ads while walking or exporting. **Draft: publish only after the Lite build and physical-device QA verify the workflow.**


## Speed-test provider clarification — Lite v1.0.0


## Local review build

The candidate uses Android SDK 26 minimum and targets API 36. The Build 98 RF Grid, Strip Chart, Map, settings, recording header and offline Help remain in the app. Band/Cell shows Android observations with radio controls disabled. Network Events & Signaling shows Android cell, service and display observations with a disabled Advanced Pro signaling preview. Indoor Walk accepts one PNG or JPEG per active survey, with three active minutes and CSV coordinates relative to the image. Outdoor sessions use five active minutes. Map tiles are off until enabled in the basemap controls.

## Speed Test providers

OpenSpeedTest Public is the hosted speed test in the release build. Cloudflare Speedtest remains QA-only pending confirmation of hosted-service terms. LibreSpeed is deferred.

Select Open Speed Test, read the disclosure, and select Start in the provider widget. OpenSpeedTest receives your IP address and test traffic. Results stay in its widget.
