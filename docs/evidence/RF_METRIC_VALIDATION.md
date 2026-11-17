# RF Metric Validation & Telemetry Provenance

**Document ID:** `RFEX-LITE-RF-VALID-20261117-V1`  
**Test Hardware:** Xiaomi 13 Pro (`2210132G`, Snapdragon 8 Gen 2 / X70 Modem)  
**Carrier:** Viettel 4G LTE (`452/04`)  
**Audit Date:** November 17, 2026

---

## 1. Serving Cell Metrics

Captured live over public Android `TelephonyManager` / `CellInfoLte`:

| RF Metric | Observed Live Value | 3GPP Nominal Range | Evaluation |
| :--- | :---: | :---: | :---: |
| **RSRP (Reference Signal Received Power)** | `-92.0 dBm` | -140 dBm to -44 dBm | Nominal (Good) |
| **RSRQ (Reference Signal Received Quality)**| `-5.0 dB` | -20 dB to -3 dB | Excellent |
| **SINR (Signal to Interference + Noise)** | `+15.0 dB` | -23 dB to +40 dB | Excellent (RRC Connected) |
| **RSSI (Received Signal Strength Indicator)**| `-61.0 dBm` | -113 dBm to -51 dBm | Strong carrier RSSI |
| **Timing Advance (TA)** | `N/A · not reported by modem (RRC Connected required)` | 0 to 1282 | Standard RRC Idle response |
| **Physical Cell ID (PCI)** | `485` | 0 to 503 | Valid LTE cell |
| **Downlink EARFCN** | `250` | 0 to 599 (Band 1) | 2135.000 MHz (DL) / 1945.000 MHz (UL) |
| **Downlink Bandwidth** | `20.000 MHz` | 1.4 to 20 MHz | Full LTE 100 PRB allocation |
| **Tracking Area Code (TAC)** | `25162` | 0 to 65535 | Valid 16-bit integer |
| **E-UTRAN Cell Identifier (ECI)** | `128011273` | 28-bit integer | eNB 500044, Sector 9 |

---

## 2. Hardware Provenance & Baseband String Sanitization

### Qualcomm Baseband Version Handling
On dual-SIM Qualcomm platforms (Snapdragon 8 Gen 2), `Build.getRadioVersion()` returns two identical comma-separated strings representing the baseband firmware of Modem 1 and Modem 2:
```text
Raw Android API Return:
MPSS.DE.3.0-Aug 17 2023-21:01:42 , MPSS.DE.3.0-Aug 17 2023-21:01:42
```
In RFeX Drive Lite v1.0.0, the radio version parser splits by comma, takes distinct tokens, and produces:
```text
Sanitized RFeX Presentation:
MPSS.DE.3.0-Aug 17 2023-21:01:42
```

---

## 3. Neighbor Cell Telemetry

Live neighbor cell reporting observed through `TelephonyManager.getAllCellInfo()`:

| Cell Type | RAT | ARFCN | Band | PCI | RSRP | RSRQ | Status |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Serving** | LTE | 250 | B1 | 485 | -92 dBm | -5 dB | Registered / Primary |
| **Neighbor 1**| LTE | 250 | B1 | 215 | -101 dBm| -11 dB | Intra-frequency neighbor |
| **Neighbor 2**| LTE | 250 | B1 | 403 | -108 dBm| -14 dB | Intra-frequency neighbor |
| **Neighbor 3**| LTE | 1700 | B3 | 312 | -112 dBm| -16 dB | Inter-frequency neighbor |

*All neighbor cells dynamically calculate their 3GPP operating band from EARFCN formulas and display clean integer signal strength.*

---

## 4. Parameters Diagnostics & Dynamic OS Provenance
- Dynamic OS readout correctly resolves `Xiaomi 2210132G (Android 13)`.
- Eliminates hardcoded device strings.
- Displays 15 kHz subcarrier spacing (SCS) and 100 kHz EARFCN raster.

---

## 5. Multi-RAT Telephony Availability
- Standalone 4G LTE mode suppresses dormant 5G NR cards to prevent confusion.
- Dual-SIM mode displays SIM1 (`Viettel 452/04`) and cleanly indicates SIM2 as `No SIM` without crashing.
