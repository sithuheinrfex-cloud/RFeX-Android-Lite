# RFeX Drive Lite — Knowledge Base & Help Center

**Product:** RFeX Drive Lite v1.0.0  
**Package:** `com.rfex.drive.lite`  
**Status:** **Approved Production Documentation** (Verified on Xiaomi 13 Pro / Android 13)

---

## 1. Quick Start & Navigation

RFeX Drive Lite operates through 6 core instrument views accessible from the bottom navigation bar:
- **RF Status:** Real-time cellular dashboard, neighbor cell list, oscillogram strip chart, and correlation scatter plot.
- **Speed Test:** User-initiated network performance diagnostics powered by OpenSpeedTest with explicit data-usage disclosures.
- **Events:** Public Android Network Events timeline (service state transitions, RAT switches, and handovers).
- **Band/Cell:** Hardware radio state observations and carrier band information (modem locking controls are Advanced Pro previews).
- **Map:** Interactive GPS drive-test mapping, keyless basemaps (OSM, Esri Satellite, Topo), cell site database, and 3GPP sector azimuth wedges.
- **Indoor:** Draft floor plan sketch studio, architectural templates, pinpoint walk testing, and on-canvas RSRP legend.

---

## 2. In-App Offline Knowledge Center (8 Categories)

Tap the `?` icon in the top header to access the 100% offline knowledge base with instant search:

1. **User Manual:** Overview of the public Android SDK architecture, 5-step onboarding, and multi-SIM operation.
2. **Drive & Indoor Testing:** Guide to conducting outdoor 5-minute drive surveys and indoor 3-minute blueprint walk tests.
3. **RF Metrics Guide:** Standard 3GPP definitions, nominal ranges, and color thresholds for RSRP, RSRQ, SINR, RSSI, TA, and CQI.
4. **Permissions & Privacy:** Detailed transparency regarding why `ACCESS_FINE_LOCATION` and `READ_PHONE_STATE` are needed, coupled with our **100% On-Device Privacy Guarantee** (zero tracking, zero analytics beacons, zero ads).
5. **Terms & Compliance:** Software freeware terms, telecommunications diagnostic disclaimers, and Google Play compliance.
6. **Troubleshooting:** Quick solutions for location acquisition, modem RRC idle states, and stationary correlation behavior.
7. **About RFeX:** Built by RF engineering enthusiasts at RFeX Technology for telecom professionals worldwide.
8. **Third-Party Notices:** Complete embedded open-source licenses (Apache-2.0, MIT, BSD, ODbL).

---

## 3. Understanding `N/A` Provenance Values

RFeX Drive Lite adheres to strict technical honesty:
- When a metric is not exposed by the device modem or the carrier network (e.g. Timing Advance when in RRC Idle, or secondary carrier SINR), Lite cleanly displays `N/A · not reported by modem (RRC Connected required)` instead of fabricating fake zeros.
- When connected to pure 4G LTE, dormant 5G NR cards are dynamically suppressed to avoid clutter.
- Stationarity is detected mathematically: when signal variance over time is zero, the correlation chart renders dots unconditionally with a dashed mean line and states `r = 0.00 (Stationary, n=60)`.
