# Android Permissions & Technical Boundaries

**Product:** RFeX Drive Lite v1.0.0  
**Package:** `com.rfex.drive.lite`  
**Status:** **Approved Production Specification**

---

## 1. Android Runtime Permissions & Purpose

RFeX Drive Lite operates strictly through standard, documented Android public SDK APIs. Each runtime permission is accompanied by an in-app transparency disclosure before requesting system access:

| Permission | Technical Requirement | In-App Disclosure & User Privacy |
| :--- | :--- | :--- |
| `ACCESS_FINE_LOCATION` | Required by Android to associate RF measurements with GPS coordinates and to expose cellular `CellInfo` and `CellIdentity` (PCI, TAC, ECI). | Clearly disclosed during Step 2 of onboarding. Users are guided to select "Precise" and "While using the app". Zero background location tracking when app is closed. |
| `READ_PHONE_STATE` | Required by Android to identify SIM slot subscriptions, carrier PLMN (`452/04`), and modem network registration states. | Reassuring disclosure in Step 3 clarifies that RFeX Drive Lite **never** makes, answers, monitors, or manages telephone calls. |
| `POST_NOTIFICATIONS` | Required on Android 13+ (API 33+) to maintain a persistent foreground service notification while outdoor drive tests are recording. | Transparent disclosure in Step 4 explaining that notifications are strictly used for drive-test session status and controls. |

---

## 2. Storage & File Access (Zero Broad Permissions)

- **Storage Access Framework (SAF):** RFeX Drive Lite does *not* request broad device storage permissions (`READ_EXTERNAL_STORAGE` or `MANAGE_EXTERNAL_STORAGE`).
- **CSV Site Imports:** Opened via system document picker (`ACTION_OPEN_DOCUMENT`).
- **CSV Survey Exports:** Saved via native document creation (`ACTION_CREATE_DOCUMENT`), allowing the user to select their desired destination in Downloads or SD card.

---

## 3. Technical Boundaries & Honest Measurement Provenance

1. **RRC Idle Timing Advance (TA):** In 3GPP LTE networks, Timing Advance is dynamically assigned by the eNodeB during active uplink transmissions. In RRC Idle or DRX sleep states, the modem halts TA updates. RFeX Drive Lite displays `N/A · not reported by modem (RRC Connected required)` instead of fabricating fake zeros.
2. **Stationary Desk Correlation:** When stationary on a desk, signal variance over time is zero, causing standard Pearson correlation formulas to divide by zero (`0/0 = NaN`). RFeX Drive Lite v1.0.0 renders points unconditionally across the grid with a dashed horizontal mean line and displays `r = 0.00 (Stationary, n=60)`.
3. **Modem Locking & Layer 3 Decoders:** Carrier locking (Band/Cell lock) and raw Layer 3 signaling (RRC/NAS PCAP decoders) require Qualcomm DIAG or root privileges and are exclusive to RFeX Drive Advanced Pro.
