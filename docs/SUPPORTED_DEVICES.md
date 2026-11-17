# Supported Android Devices & Hardware Compatibility

**Product:** RFeX Drive Lite v1.0.0  
**Package:** `com.rfex.drive.lite`  
**Minimum Android Version:** Android 8.0 Oreo (API level 26)  
**Target / Tested Android Version:** Android 13–16 (API level 33–36)

---

## 1. Operating System & SDK Requirements

| Parameter | Specification | Notes |
| :--- | :--- | :--- |
| **Minimum SDK** | API 26 (Android 8.0 Oreo) | Full legacy telephony backward compatibility |
| **Target SDK** | API 36 (Android 16 Vanilla Ice Cream) | Fully compliant with Google Play target API requirements |
| **Root Requirement** | None (Zero Root Required) | 100% public Android SDK API execution |
| **Architecture** | 64-bit / 32-bit agnostic | Pure Kotlin/Java byte-code, runs on ARM64, ARMv7, x86_64 |

---

## 2. Tested & Verified Reference Hardware

### Primary Reference Device
- **Model:** Xiaomi 13 Pro (`2210132G`)
- **Chipset:** Qualcomm Snapdragon 8 Gen 2 (SM8550-AB)
- **Modem:** Snapdragon X70 5G Modem-RF System (`MPSS.DE.3.0`)
- **Android Version:** Android 13 (MIUI 14 Global)
- **Carrier Environment:** Viettel 4G LTE (`452/04`)
- **Verification Result:** `100% PASS` — Verified across all instruments, basemaps, indoor walk tests, and CSV export.

### General Android Device Compatibility

Because RFeX Drive Lite is built strictly upon standard Android public APIs (`TelephonyManager`, `SubscriptionManager`, `LocationManager`), it is compatible with Android devices manufactured by:
- **Google Pixel** (Pixel 6, 7, 8, 9 series)
- **Samsung Galaxy** (Galaxy S20 through S25 series, A-series, Z Fold/Flip)
- **Xiaomi / Redmi / POCO** (Snapdragon and MediaTek platforms)
- **OnePlus / OPPO / Realme**
- **Motorola / Sony / ASUS**

---

## 3. Hardware-Dependent Features & Modem Limitations

1. **Carrier Aggregation (CA):** Secondary component carriers (SCC) are displayed when reported by the device's Android Radio Interface Layer (RIL). Some OEM Android builds restrict SCC reporting to active heavy data transfer states.
2. **Timing Advance (TA):** Reported when UE is in RRC Connected mode. When the modem enters RRC Idle or DRX sleep mode, Android reports TA as unavailable (`N/A`).
3. **5G NR Standalone (SA) vs Non-Standalone (NSA):** NSA dual-connectivity (EN-DC) displays LTE anchor cell metrics alongside 5G availability indicators. 5G SA displays native NR-ARFCN, SS-RSRP, SS-RSRQ, and SS-SINR when connected.
4. **Dual-SIM Operation:** Fully supports dual physical SIMs and eSIMs where reported by `SubscriptionManager`.
