# Historical Defect Closure & Resolution Summary

**Document ID:** `RFEX-LITE-DEFECT-CLOSURE-20261117-V1`  
**Application:** RFeX Drive Lite v1.0.0  
**Audit Date:** November 17, 2026

This summary documents the complete remediation of all defects identified during historical benchmark audits and initial release candidate testing:

---

| Issue ID | Historical Finding | Final Source Fix | Final Verification Test | Verified Evidence | Status |
| :---: | :--- | :--- | :--- | :--- | :---: |
| **LIT-01** | Missing SINR acquisition in early builds | Acquired live LTE SINR via `CellSignalStrengthLte.getSinr()` with dB conversion | Live on Viettel 4G LTE | [05-rf-dashboard.png](../screenshots/05-rf-dashboard.png) (`+15.0 dB`) | **CLOSED** |
| **LIT-02** | Google Maps tile scraping (`mt0.google.com`) | Purged tile scraping; replaced with policy-compliant OpenStreetMap Standard | Map rendering on physical device | [10-live-map.png](../screenshots/10-live-map.png) | **CLOSED** |
| **LIT-03** | CARTO CDN hosted tile dependency | Completely purged `basemaps.cartocdn.com`; replaced with keyless OSM, Esri, Topo | Basemap switching dialog | [12-map-layers-legend.png](../screenshots/12-map-layers-legend.png) | **CLOSED** |
| **LIT-04** | Residual DIAG bytecode in repository | Eradicated Python `.pyc` from Git trees and enforced `.gitignore` | Bytecode audit | Verified zero `.pyc` in tree | **CLOSED** |
| **LIT-05** | Double Qualcomm baseband version string | Deduplicated comma-separated radio strings via `.distinct()` in `DashboardScreen.kt` | Screen inspection on Xiaomi 13 Pro | [06-serving-cell-details.png](../screenshots/06-serving-cell-details.png) | **CLOSED** |
| **LIT-06** | Saved Sessions character stacking | Added `weight(1f, fill=false)` and `softWrap=false` in `SavedSessionsDialog.kt` | Open Saved Sessions Manager | [16-saved-sessions.png](../screenshots/16-saved-sessions.png) | **CLOSED** |
| **LIT-07** | Blueprint title block UTF-8 mojibake | Cleaned title block ASCII string in `FloorplanSketchDialog.kt` | Blueprint template load | [18-indoor-floorplan-sketch.png](../screenshots/18-indoor-floorplan-sketch.png) | **CLOSED** |
| **LIT-08** | Stationary correlation scatter plot blank | Render scatter points unconditionally with dashed mean line and r=0.00 readout | Desk test on Xiaomi 13 Pro | [09-rf-correlation-scatter.png](../screenshots/09-rf-correlation-scatter.png) | **CLOSED** |
| **LIT-09** | Lack of serving/neighbor spider links | Added 1-tap `[ LOAD SAMPLE SITES (3 SITES) ]` in `CellFileManager.kt` | Map cell DB dialog | [13-cell-csv-import.png](../screenshots/13-cell-csv-import.png) | **CLOSED** |
| **LIT-10** | Informal `(may be idle)` remark | Replaced with standard 3GPP wording `N/A · not reported by modem (RRC Connected required)` | Radio state inspect | Verified in `RadioReadOnlyScreens.kt` | **CLOSED** |
| **LIT-11** | No indoor walk clear / reset action | Added `Clear` button next to `Undo pin` with confirmation dialog in `IndoorSurvey.kt` | Pin and clear 3 points | [20-indoor-cleared-reset.png](../screenshots/20-indoor-cleared-reset.png) | **CLOSED** |
| **LIT-12** | Missing indoor RF KPI legend | Added compact on-canvas **Indoor RSRP Legend** (`≥-75`, `-85`, `-95`, `<-95`) | Indoor walk canvas | [19-indoor-walk-survey.png](../screenshots/19-indoor-walk-survey.png) | **CLOSED** |
| **LIT-13** | Residual advertising copy in help center | Purged all `LiteAds` references; added 100% On-Device Privacy Guarantee | Help center inspect | [23-privacy-on-device-guarantee.png](../screenshots/23-privacy-on-device-guarantee.png) | **CLOSED** |
