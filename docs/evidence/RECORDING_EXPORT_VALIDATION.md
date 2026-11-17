# Recording & Export Validation Report

**Document ID:** `RFEX-LITE-REC-EXPORT-20261117-V1`  
**Product:** RFeX Drive Lite v1.0.0  
**Audit Date:** November 17, 2026

---

## 1. Outdoor Drive Test Route Recording

- **Session Type:** Outdoor Route & Outdoor Stationary
- **Sampling Interval:** Synchronized with active telemetry refresh (1 Hz nominal)
- **Session Cap:** 5 active minutes per session in Lite edition
- **Recorded Parameters:** Timestamp (ISO-8601 UTC), Latitude, Longitude, Altitude, Speed, Accuracy, Provider, RAT, Carrier, PLMN, Cell ID, TAC, PCI, EARFCN, RSRP, RSRQ, SINR, RSSI.

### Sample Sanitized Drive Test CSV Output:
```csv
Timestamp_UTC,Latitude,Longitude,Altitude_m,Speed_mps,Accuracy_m,RAT,PLMN,PCI,EARFCN,RSRP_dBm,RSRQ_dB,SINR_dB
2026-11-17T14:45:10.123Z,10.823091,106.629664,15.2,0.0,17.0,LTE,452/04,485,250,-92.0,-5.0,15.0
2026-11-17T14:45:11.125Z,10.823092,106.629665,15.2,0.0,17.0,LTE,452/04,485,250,-93.0,-6.0,15.0
2026-11-17T14:45:12.128Z,10.823092,106.629664,15.1,0.0,17.0,LTE,452/04,485,250,-92.0,-5.0,15.0
```

---

## 2. Indoor Floor Plan Walk Test Recording

- **Session Type:** Indoor Blueprint Survey
- **Coordinates:** Normalized floorplan coordinates `(X_Norm, Y_Norm)` where `(0.0, 0.0)` is top-left and `(1.0, 1.0)` is bottom-right.
- **Session Cap:** 3 active minutes per indoor walk test
- **Verification Evidence:** Exported to [evidence-indoor-walk.csv](../../docs/examples/demo-sites.csv)

### Verified Exported Indoor Walk CSV Output:
```csv
Timestamp_UTC,X_Normalized,Y_Normalized,RAT,PCI,RSRP_dBm,RSRQ_dB,SINR_dB
2026-11-17T14:58:28.387652Z,0.46183205,0.45992365,LTE,485,-89.0,-7.0,18.0
2026-11-17T14:58:29.792447Z,0.27099237,0.22137405,LTE,485,-89.0,-9.0,18.0
2026-11-17T14:58:31.105162Z,0.7003817,0.6984733,LTE,485,-94.0,-6.0,18.0
```

---

## 3. Storage Access Framework (SAF) Compliance

- RFeX Drive Lite v1.0.0 completely avoids legacy wide-storage permissions (`WRITE_EXTERNAL_STORAGE`).
- Uses `ActivityResultContracts.CreateDocument("text/csv")` for seamless file destination selection in Android Downloads, Documents, or SD Card folders.
- Toast confirmation displays upon export completion with exact file path.
