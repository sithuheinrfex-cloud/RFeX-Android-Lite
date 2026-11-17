# UI & Visual Regression Verification Results

**Document ID:** `RFEX-LITE-UI-REGRESS-20261117-V1`  
**Product:** RFeX Drive Lite v1.0.0  
**Audit Date:** November 17, 2026

---

## 1. Resolved Visual & Layout Regressions

### A. Saved Sessions Manager Character-by-Character Vertical Wrapping
- **Defect Description:** In previous release candidates, the session size badge string (`20 pts • 1.0 KB`) wrapped character-by-character vertically (`2\n0\np\nt\ns\n...\nK\nB`) due to unconstrained row width and lack of weights.
- **Root Cause Fix:** In `SavedSessionsDialog.kt`, added `Modifier.weight(1f, fill = false)` with `overflow = TextOverflow.Ellipsis` to the session ID row and constrained the metric text with `softWrap = false, maxLines = 1`.
- **Verified State:** Horizontal layout renders cleanly as `20 pts • 1.0 KB` across all screen resolutions and font sizes. *(Evidence: [16-saved-sessions.png](../screenshots/16-saved-sessions.png))*

### B. Blueprint Title Block UTF-8 Mojibake
- **Defect Description:** Floor plan sketch canvas exhibited corrupted bullet characters (`â€¢`) in the title block.
- **Root Cause Fix:** In `FloorplanSketchDialog.kt`, replaced UTF-8 bullet sequences with clean ASCII separators: `"RFeX DRIVE LITE - DRAFT FLOOR PLAN"` and `"ARCHITECTURAL BLUEPRINT GRID | INDOOR WALK TEST"`.
- **Verified State:** Blueprint renders sharp, clean engineering typography without encoding artifacts. *(Evidence: [18-indoor-floorplan-sketch.png](../screenshots/18-indoor-floorplan-sketch.png))*

### C. Correlation Scatter Plot Blank Canvas Fix
- **Defect Description:** When stationary desk testing, signal variance is 0, causing Pearson correlation calculation `r` to evaluate as `NaN`. Gating point rendering behind `isValid` hid all active measurement dots.
- **Root Cause Fix:** In `DashboardScreen.kt`, scatter points are now rendered unconditionally regardless of variance. When stationary, a dashed horizontal mean line is drawn, and readout states `r = 0.00 (Stationary, n=60)`.
- **Verified State:** Verified live on Xiaomi 13 Pro. *(Evidence: [09-rf-correlation-scatter.png](../screenshots/09-rf-correlation-scatter.png))*

### D. Parameters Tab Layout & Dual-Modem String Truncation
- **Defect Description:** Double Qualcomm modem radio version caused table cell text truncation and horizontal misalignment.
- **Root Cause Fix:** In `DashboardScreen.kt`, comma-separated duplicate radio versions are split and deduplicated, and table rows use standard proportional weights.
- **Verified State:** Clean single baseband version string displayed without overflow. *(Evidence: [06-serving-cell-details.png](../screenshots/06-serving-cell-details.png))*

### E. Residual Advertising Copy Purge
- **Defect Description:** Leftover ad consent strings (*"Google handles ad consent where ads are configured"*) lingered from legacy template code.
- **Root Cause Fix:** Eradicated all `LiteAds` references from `HelpCenterScreen.kt` and strings resources. Replaced with explicit **100% On-Device Privacy Guarantee**.
- **Verified State:** Verified zero ad mentions in help center and zero ad SDKs in APK. *(Evidence: [23-privacy-on-device-guarantee.png](../screenshots/23-privacy-on-device-guarantee.png))*
