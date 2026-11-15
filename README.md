# RFeX Drive Lite

**Android cellular and RF monitoring using documented Android SDK APIs.**

> **Release status:** v1.0.0 in preparation. This public repository is for product information and documentation. There is no released Lite Android binary or public source license here yet.

RFeX Drive Lite is the planned free-to-install edition of the RFeX Drive product family. It focuses on practical cellular field observations on compatible Android phones without root, modem diagnostics or proprietary modem-access interfaces. Its live measurements depend on what the Android device, Android version, operator and granted permissions expose.

## Planned Lite v1.0.0 features

| Feature | Planned Lite scope |
|---|---|
| Live cellular status | Serving cell and basic neighbor information when exposed by Android |
| 2G / 3G / 4G / 5G | Public-API values supported by the phone and network; unavailable fields shown as N/A |
| RF/GNSS map | Online basemap, real location, route-point coloring based on genuine measurements |
| Cell database | CSV only; up to **100 distinct site points** |
| Sector preview | Up to **three selected sites** using actual sector azimuth/beamwidth values where present |
| Session recording | **Five actual recorded minutes per session**, unlimited separately saved sessions |
| Export | CSV and GPX for completed sessions (when implemented and validated) |
| Connectivity | User-triggered ping and a single optional download/upload speed test with disclosure |
| Advertising | Gentle AdMob placements on idle screens, not during tests or recording |
| Demo mode | Explicitly labeled sample data, never presented as live network measurements |

### Not included

Existing Band Lock and Cell Lock screens remain as read-only radio information panels with disabled Pro/Advanced previews. The existing Signaling screen shows **genuine public Android Network Events**, not decoded modem protocol messages. No raw RRC/NAS/L3 capture or decoder, Qualcomm DIAG/QMDL, Pycrate, Chaquopy, root commands, hidden/vendor modem APIs, *actual* band/ARFCN/cell locking, PCTEL scanner integration, KML/KMZ/XML cell-file import or full RF simulation are shipped.

## Documentation

- [Technical datasheet](docs/DATASHEET.md)
- [User manual](docs/USER_MANUAL.md)
- [CSV site-file guide](docs/CSV_SITE_FORMAT.md)
- [Permissions and measurement limitations](docs/PERMISSIONS_AND_LIMITATIONS.md)
- [FAQ and support](docs/FAQ.md)
- [Privacy information for the review build](docs/PRIVACY_REVIEW.md)
- [Release notes](docs/RELEASE_NOTES.md)

## Official websites (planned routes)

- Product: https://rfex.app/drive/lite/
- Docs: https://docs.rfex.app/drive/lite/
- Privacy: https://rfex.app/drive/lite/privacy/
- Support: https://rfex.app/drive/lite/support/

**Google Play:** Listing URL to be added *only after the real app is published and its package ID verified*. No direct APK download is offered here at this stage.

## Project and licensing boundaries

This public documentation repository is independent of the proprietary `rfex-platform` repository. **Public visibility does not mean the Kotlin source is open source**. No source code distribution license has been granted by publishing this documentation. See [Publication and copyright](COPYRIGHT.md). Third-party notices must be generated from the *actual signed Lite release dependency graph* before launch.

Copyright © 2026 RFeX. Product and technical details are subject to the verified v1.0.0 release.


## Help and verified device compatibility

- [Help Center (draft)](docs/HELP_CENTER.md)
- [Device compatibility — verification pending](docs/SUPPORTED_DEVICES_REVIEW_REQUIRED.md)

Device screenshots and specific Xiaomi 13 Pro validation results will be linked **only after testing of the actual Lite app** and a public privacy review. No internal QA screenshots, operator site databases, precise GNSS tracks or private device identifiers should be included here.

## Indoor Walk — Lite v1.0.0 (implementation-dependent draft)

Indoor Walk reuses the Build 98 floorplan screen. In Lite, import **one PNG/JPEG floorplan** per session, manually tap survey points while real Android-public-API cell measurements are available, and record for up to **3 minutes of active recording time**. You may start additional separately saved sessions without a daily session count. Export genuine recorded points as **CSV**. Tap positions are relative floorplan image positions, **not GPS positions or calibrated surveyed distances**. Multilevel floorplan workflows, georeferencing/advanced calibration and professional reports are Pro/Advanced feature previews only. No ads while walking or exporting. **Draft: publish only after the Lite build and physical-device QA verify the workflow.**

## Local review build

The candidate uses Android SDK 26 minimum and targets API 36. The Build 98 RF Grid, Strip Chart, Map, settings, recording header and offline Help remain in the app. Band/Cell shows Android observations with radio controls disabled. Network Events & Signaling shows Android cell, service and display observations with a disabled Advanced Pro signaling preview. Indoor Walk accepts one PNG or JPEG per active survey, with three active minutes and CSV coordinates relative to the image. Outdoor sessions use five active minutes. Map tiles are off until enabled in the basemap controls.

## Speed Test providers

OpenSpeedTest Public is the hosted speed test in the release build. Cloudflare Speedtest remains QA-only pending confirmation of hosted-service terms. LibreSpeed is deferred.

Select Open Speed Test, read the disclosure, and select Start in the provider widget. OpenSpeedTest receives your IP address and test traffic. Results stay in its widget.
