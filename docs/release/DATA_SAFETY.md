# Google Play Data Safety Declaration Worksheet

**Application:** RFeX Drive Lite  
**Application ID:** `com.rfex.drive.lite`  
**Version:** 1.0.0 (Version Code 1)  
**Date:** November 16, 2026  

Use this exact worksheet when completing the Data Safety section in the Google Play Console.

---

## 1. Overview Questions

| Question | Answer | Justification |
|---|---|---|
| **Does your app collect or share any of the required user data types?** | **Yes** | The app accesses Approximate and Precise Location to provide live mapping and record drive-test measurements. |
| **Is all of the user data collected by your app encrypted in transit?** | **Yes** | All external HTTP communications (map tile fetching, speed testing) use standard TLS/HTTPS encryption. |
| **Do you provide a way for users to request that their data be deleted?** | **Yes** | All recorded session data is stored locally on the device; users can delete files in-app or clear app data via Android Settings. |

---

## 2. Data Types & Declarations

### Category: Location

#### Data Type: Approximate Location (`ACCESS_COARSE_LOCATION`)
- **Collected?** Yes
- **Shared?** No (Data is not shared with any third party)
- **Is this data processed ephemerally?** No (Saved to local CSV only when the user explicitly triggers recording; otherwise ephemeral in memory)
- **Is this data required for your app, or can users choose whether it's collected?** Required for map-based RF positioning features (users can deny permission and use dashboard-only mode)
- **Purposes for collection:**
  - **App functionality:** Displaying cellular signal measurements on a map and logging coordinates to user-initiated drive-test session files.

#### Data Type: Precise Location (`ACCESS_FINE_LOCATION`, `ACCESS_BACKGROUND_LOCATION`)
- **Collected?** Yes
- **Shared?** No (Data is not shared with any third party)
- **Is this data processed ephemerally?** No (Saved to local CSV only when the user explicitly triggers recording; otherwise ephemeral in memory)
- **Is this data required for your app, or can users choose whether it's collected?** Required for precise RF drive testing (users can deny permission and use dashboard-only mode)
- **Purposes for collection:**
  - **App functionality:** Displaying cellular signal measurements on a map, positioning the user location puck, and logging GNSS coordinates during stationary or drive surveys.

---

## 3. Categories with ZERO Collection

The following data types are **NOT** collected or shared by RFeX Drive Lite:

- **Personal Info:** Name, Email, Address, Phone number, User IDs, Race/ethnicity, Political/religious beliefs, Sexual orientation (NONE collected).
- **Financial Info:** Credit card, Bank account, Purchase history, Credit info (NONE collected).
- **Health & Fitness:** Health info, Fitness info (NONE collected).
- **Messages:** Emails, SMS/MMS, Other in-app messages (NONE collected).
- **Photos and Videos:** Photos, Videos (NONE collected).
- **Audio Files:** Voice/sound recordings, Music files (NONE collected).
- **Files and Docs:** User files are processed strictly locally when importing site CSVs or floorplan images; no files are uploaded to external servers.
- **Calendar:** Calendar events (NONE collected).
- **Contacts:** Contacts list (NONE collected).
- **App Activity:** Page views, In-app search, Installed apps (NONE collected).
- **Web Browsing:** Browsing history (NONE collected).
- **App Info & Performance:** Crash logs, Diagnostics, Other app performance data (NONE collected via automated SDKs).
- **Device or Other Identifiers:** IMEI, MAC address, Advertising ID, Device ID (NONE collected).

---

## 4. Google Play Store Privacy Policy Link

- **Privacy Policy URL to submit in Play Console:**  
  `https://rfex.app/drive/lite/privacy/`
