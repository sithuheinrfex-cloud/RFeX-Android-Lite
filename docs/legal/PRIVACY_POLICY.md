# Privacy Policy for RFeX Drive Lite

**Last Updated:** November 16, 2026  
**Effective Date:** November 16, 2026  
**Application ID:** `com.rfex.drive.lite`  
**Developer:** RFeX Software  
**Contact:** privacy@rfex.app  

---

## 1. Introduction

RFeX Drive Lite ("the Application") is an Android cellular and radio frequency (RF) observation tool engineered with a strict **local-first, privacy-by-design** architecture. RFeX Drive Lite does not sell, lease, or monetize your personal data. 

This Privacy Policy outlines how the Application collects, uses, and protects data when installed on your mobile device.

---

## 2. Information Handled by the Application

### A. Location Information (Approximate & Precise)
- **What is accessed:** The Application requests Android runtime permissions for `ACCESS_FINE_LOCATION`, `ACCESS_COARSE_LOCATION`, and `ACCESS_BACKGROUND_LOCATION`.
- **Purpose:** Location coordinates are used strictly on-device to:
  1. Display your current location puck and orientation on the map view.
  2. Associate geographic coordinates with cellular signal measurements (RSRP, RSRQ, RSSI, SINR) during live monitoring.
  3. Record route breadcrumbs into user-initiated drive-test CSV files stored locally on your device.
- **Data Retention & Transmission:** **Your location data is never transmitted to RFeX servers, external analytics systems, or third parties.** Recorded sessions remain exclusively in your device's local application storage until you choose to export or delete them.

### B. Telephony & Cellular Network State
- **What is accessed:** Cell tower identifiers (PCI, TAC, CI, eNB/gNodeB ID, ARFCN) and signal parameters exposed via public Android SDK `TelephonyManager` APIs.
- **Purpose:** Displaying real-time cellular engineering diagnostics on your device screen and logging them into local CSV drive-test session files.
- **Data Retention & Transmission:** Cellular diagnostic data is processed locally in device RAM and written to local storage only during an active recording session. No cellular data is transmitted externally.

### C. Device & Hardware Identifiers
- **What is accessed:** Device model, manufacturer, and Android OS version.
- **What is NOT accessed:** The Application **does not access** IMEI, IMSI, SIM serial numbers, phone numbers, or persistent hardware identifiers.

---

## 3. External Network Communications

The Application initiates external network requests only in the following specific scenarios:

1. **Map Basemap Tiles:**  
   When map display is enabled, the Application fetches raster map tiles from public cartography services:
   - **OpenStreetMap:** Standard and Humanitarian raster tiles hosted via OpenStreetMap and OSM France (Subject to OpenStreetMap Foundation Privacy Policy).
   - **NASA Blue Marble:** Overview satellite tiles (Public Domain).
   - *Data transmitted:* Standard HTTP request headers, requested tile coordinates (Z/X/Y), and your device IP address as required to deliver web content.

2. **User-Initiated Speed Test (OpenSpeedTest):**  
   If you explicitly choose to launch the OpenSpeedTest tool, network traffic is generated between your device and public OpenSpeedTest servers to measure latency, download bitrate, and upload bitrate.
   - *Data transmitted:* Test network traffic and device IP address.
   - *Disclosure:* A modal disclosure is displayed before any test traffic is generated.

3. **Crash Reporting and Analytics:**  
   RFeX Drive Lite **contains zero third-party analytics SDKs, zero telemetry trackers, and zero advertising SDKs** in this release.

---

## 4. Data Storage and User Control

- **Local Storage:** All drive-test sessions, indoor survey records, and imported cell site files are stored locally in the application's private sandbox (`Android/data/com.rfex.drive.lite/files/`).
- **User Deletion:** You can delete any saved survey session or imported file at any time from within the application UI, or permanently remove all data by uninstalling the Application or clearing application storage in Android Settings.

---

## 5. Children's Privacy

The Application is a specialized technical tool for telecommunications and RF engineering professionals. It is not directed to children under the age of 13, and does not knowingly collect personal information from children.

---

## 6. Changes to this Privacy Policy

We may update this Privacy Policy periodically. Any modifications will be reflected in the updated policy file within the application and published on the official documentation portal.

---

## 7. Contact Information

For inquiries regarding this Privacy Policy or data privacy in RFeX Drive Lite, please contact:  
**Email:** privacy@rfex.app  
**Website:** https://rfex.app/drive/lite/privacy/
