# RFeX Drive Lite — Help Center (v1.0.0 candidate)

**Status: documentation draft for a not-yet-verified Lite build.** The final in-app Help must be tested before publishing this page.

Start with the [User Manual](USER_MANUAL.md), [Technical Datasheet](DATASHEET.md), [CSV format](CSV_SITE_FORMAT.md), [Permissions and limitations](PERMISSIONS_AND_LIMITATIONS.md), and [FAQ](FAQ.md).

## Quick start

Open the Lite app; allow location and other permissions only when the feature requires them. Review live RF metrics where your phone exposes them, open the RF map and select the layers you want. Use a CSV of up to 100 unique sites; preview sectors for up to three selected sites if azimuth/beamwidth data is valid. Start a recording and stop or let it auto-save after five minutes of recorded time, then export CSV/GPX with the Android file picker.

## Understanding N/A and missing cells

Lite shows network information through publicly documented Android APIs. Android/device/SIM/carrier policy may limit 5G measurements or neighbor cells. `N/A` means no trustworthy current reading is available, not a measured zero.

## Band Lock, Cell Lock and Signaling screens

These familiar Build 98 screens remain in Lite. **Band Lock** and **Cell Lock** show read-only observed band, channel, serving cell and neighbors where Android exposes them, with locking controls clearly labeled **Pro/Advanced preview — unavailable in Lite**. **Signaling** offers an **Android Network Events** timeline of genuine public-API service state, signal changes and observed serving-cell changes. This is not an RRC/NAS log or a decoded handover cause. RRC/NAS decoders, Qualcomm DIAG, Pycrate/Chaquopy, root, AT commands, actual modem locking and scanner control are **not included in Lite**.

## Help inside the app

Offline Help has a single-line search across installed topics and a horizontally scrollable category row. Select Third-Party Notices to read the bundled licenses. The active category or Search results appears above the matching topics.

For assistance, use the planned [RFeX Lite support page](https://rfex.app/drive/lite/support/), which must be verified as live before release.

## Indoor Walk — Lite v1.0.0 (implementation-dependent draft)

Indoor Walk reuses the Build 98 floorplan screen. In Lite, import **one PNG/JPEG floorplan** per session, manually tap survey points while real Android-public-API cell measurements are available, and record for up to **3 minutes of active recording time**. You may start additional separately saved sessions without a daily session count. Export genuine recorded points as **CSV**. Tap positions are relative floorplan image positions, **not GPS positions or calibrated surveyed distances**. Multilevel floorplan workflows, georeferencing/advanced calibration and professional reports are Pro/Advanced feature previews only. No ads while walking or exporting. **Draft: publish only after the Lite build and physical-device QA verify the workflow.**


## Speed Test and Server FAQ (to align after Lite release audit)

- **Can I use an Ookla server?** Lite does not claim licensed embedded Ookla SDK or arbitrary use of Ookla infrastructure.
- **Will speed testing use mobile data?** Yes. A test must start only on user request, with a data-usage warning and cancellation.
- **Are speeds comparable across providers?** Not necessarily; results depend on test method, server, stream count and network conditions.

## Local review build

The candidate uses Android SDK 26 minimum and targets API 36. The Build 98 RF Grid, Strip Chart, Map, settings, recording header and offline Help remain in the app. Band/Cell shows Android observations with radio controls disabled. Network Events & Signaling shows Android cell, service and display observations with a disabled Advanced Pro signaling preview. Indoor Walk accepts one PNG or JPEG per active survey, with three active minutes and CSV coordinates relative to the image. Outdoor sessions use five active minutes. Map tiles are off until enabled in the basemap controls.

## Speed Test providers

OpenSpeedTest Public is the hosted speed test in the release build. Cloudflare Speedtest remains QA-only pending confirmation of hosted-service terms. LibreSpeed is deferred.

Select Open Speed Test, read the disclosure, and select Start in the provider widget. OpenSpeedTest receives your IP address and test traffic. Results stay in its widget.
