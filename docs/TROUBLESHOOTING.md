# RFeX Drive Lite — Troubleshooting & Field Diagnostics Guide

**Product:** RFeX Drive Lite v1.0.0  
**Package:** `com.rfex.drive.lite`

---

## 1. Permission & Location Issues

### Issue: "Location Provider Unavailable" or GPS Not Updating
- **Cause:** Android Location Services are disabled or set to "Battery Saver / Network Only" mode.
- **Resolution:** 
  1. Open Android **Settings > Location** and ensure Location is **ON**.
  2. In RFeX Drive Lite, verify that `ACCESS_FINE_LOCATION` is granted.
  3. Step outside or move away from heavy concrete structures to allow satellite signal acquisition. The GPS status indicator in the top header will transition from `NET` to `GPS` with active satellite count (e.g. `12SAT ±3m`).

### Issue: Missing Phone State / No Carrier Name Displayed
- **Cause:** `READ_PHONE_STATE` permission was denied during onboarding.
- **Resolution:** Open Android **Settings > Apps > RFeX Drive Lite > Permissions** and set **Phone** to **Allow**.

---

## 2. RF Telemetry & Measurement Observations

### Issue: RSRP is Updating but SINR Shows `N/A`
- **Cause:** UE is in an idle state or connected to a legacy base station whose HAL does not report SINR for the current radio access technology.
- **Resolution:** Initiate a background data stream (e.g., speed test or ping) to transition the UE modem from RRC Idle into RRC Connected mode. On LTE networks, SINR will populate immediately (e.g. `+15.0 dB`).

### Issue: Correlation Scatter Plot Shows `r = 0.00 (Stationary)`
- **Cause:** When the device is stationary on a desk, signal variance over time is near zero, making standard Pearson correlation trendlines mathematically undefined (0/0).
- **Resolution:** RFeX Drive Lite v1.0.0 renders points unconditionally with a dashed horizontal mean line and displays `r = 0.00 (Stationary, n=60)`. When moving in a vehicle or walking, dynamic signal variations will immediately plot a live linear regression trendline with calculated Pearson `r`.

### Issue: Neighbor Cells List is Empty
- **Cause:** The mobile network operator may not have configured intra-frequency neighbor cell broadcasting on the serving carrier, or the device is in deep battery saver mode.
- **Resolution:** Verify that Android Battery Optimization for RFeX Drive Lite is set to "Unrestricted" so the OS allows frequent telephony cell polling.

---

## 3. Basemaps & Site Visualization

### Issue: Basemap Appears Blank or Shows Grid Only
- **Cause:** Cellular or Wi-Fi data is disconnected, preventing initial tile download.
- **Resolution:** Re-enable mobile data or connect to Wi-Fi. Alternatively, switch to the `Off / Grid` basemap mode to view live GPS breadcrumbs and RF points without requiring internet.

### Issue: No Sector Wedges or Spider Lines Visible on Map
- **Cause:** No cell database has been loaded into memory.
- **Resolution:** Open `CELL DB` dialog from the top header or map controls and tap `[ LOAD SAMPLE SITES (3 SITES) ]`. Three realistic local LTE sites matching your serving PCI and neighbor PCIs will populate, activating 3GPP antenna wedges and live spider lines (`LINKS: ON`).

---

## 4. Indoor Walk Survey

### Issue: Cannot Tap "USE AS FLOORPLAN" in Draft Sketch Studio
- **Cause:** Canvas is empty (no walls or rooms drawn yet).
- **Resolution:** Select a template via `[ TEMPLATES ]` (e.g. `Central Corridor & 4 Offices`) or draw at least one wall using the `WALL` or `ROOM` tool. Once drawn, `USE AS FLOORPLAN` will become active.

### Issue: Placed Incorrect Pinpoints on Floorplan
- **Resolution:**
  - Tap `Undo pin` to remove the last dropped pinpoint.
  - Tap `Clear` to open the confirmation dialog and reset all pinpoints to 0 while preserving the active floorplan.
