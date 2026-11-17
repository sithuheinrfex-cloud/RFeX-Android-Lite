# Frequently Asked Questions (FAQ) — RFeX Drive Lite

**Product:** RFeX Drive Lite v1.0.0  
**Status:** **Approved Production FAQ**

---

### General & Distribution

**Q: What does RFeX Drive Lite cost?**  
**A:** RFeX Drive Lite is **100% free** to install and use. It contains **zero in-app purchases, zero subscription tiers, and zero advertisements**.

**Q: What Android versions and devices are supported?**  
**A:** RFeX Drive Lite requires Android 8.0 Oreo (API 26) or higher, targets Android 16 (API 36), and is thoroughly verified on modern Android 13/14 devices including the Xiaomi 13 Pro (Snapdragon 8 Gen 2).

**Q: Where can I download RFeX Drive Lite?**  
**A:** The application is distributed officially through the Google Play Store for verified Android devices. Standalone signed release APKs are also provided for direct sideloading and enterprise testing on GitHub.

---

### Telemetry & Measurements

**Q: Why do some signal fields show `N/A`?**  
**A:** RFeX Drive Lite operates strictly through standard Android public APIs. When a metric is not reported by your device's modem hardware or the mobile carrier (such as Timing Advance when in RRC Idle, or secondary component carrier SINR), Lite honestly displays `N/A · not reported by modem (RRC Connected required)` rather than inventing fake data.

**Q: Can Lite decode Layer 3 signaling or lock LTE bands?**  
**A:** No. Layer 3 protocol decoding (RRC/NAS PCAP) and active band/cell locking require modem baseband access or Qualcomm DIAG interfaces with root privileges. These capabilities are exclusive to RFeX Drive Advanced Pro.

**Q: How does the correlation scatter plot work when stationary?**  
**A:** When sitting stationary on a desk, signal variance over time is zero, causing Pearson correlation formulas to divide by zero (`0/0`). RFeX Drive Lite v1.0.0 renders points unconditionally across the grid with a dashed horizontal mean line and displays `r = 0.00 (Stationary, n=60)`. When in motion, a live linear regression trendline with calculated Pearson `r` is plotted dynamically.

---

### Maps, Cell Sites & Indoor Surveys

**Q: Do the map basemaps require API keys or accounts?**  
**A:** No. All basemaps (OpenStreetMap Standard, Humanitarian OSM, Esri World Imagery, OpenTopoMap) are 100% free and keyless. No account registration, billing, or subscription is required. For offline operation, select the `Off / Grid` mode.

**Q: How do I display sector wedges and spider lines?**  
**A:** Open the `CELL DB` dialog and tap `[ LOAD SAMPLE SITES (3 SITES) ]`. Three realistic local LTE sites matching your serving PCI and neighbor PCIs will generate immediately, activating 3GPP antenna azimuth wedges and live serving line-of-sight spider links (`LINKS: ON`). Alternatively, import your own custom site list via CSV (up to 100 sites).

**Q: How do I clear indoor walk test points without losing my floorplan?**  
**A:** On the Indoor tab, tap the `Clear` button next to `Undo pin`. A confirmation dialog (`Clear All Pinpoints?`) will prompt you to confirm, resetting survey pinpoints to 0 while preserving your loaded floorplan sketch.

---

### Privacy & Data Security

**Q: Does RFeX Drive Lite collect my location or telemetry?**  
**A:** **No.** RFeX Drive Lite features a strict **100% On-Device Privacy Guarantee**. All GPS coordinates, RF measurements, and survey logs remain strictly on your physical device. Zero data is transmitted to RFeX servers or third parties.
