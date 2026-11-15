# RFeX Drive Lite v1.0.0 review

Package com.rfex.drive.lite, version code 1, version name 1.0.0, min SDK 26, target SDK 36. The final stabilization audit resolved remaining UI, map coordinate fallback, manual network tools, and Help Center defects while preserving Build 98 UI/UX and 124-component dependency boundaries.

Key updates:
- Map & RF Point Rendering: Resolved coordinate resolution and filtering so recorded RF points and track polylines reliably render over the fallback grid even when basemap tiles are unavailable. Explicit status pills for "No RF points recorded yet." and "No cell database loaded."
- Basemap Investigation: Confirmed tile.openstreetmap.org DNS sinkhole (127.0.0.1) on local LAN router; NASA Blue Marble satellite overview remains functional.
- Manual Network Test Tools: Added user-initiated Manual Call (ACTION_DIAL) and Manual SMS (ACTION_SENDTO smsto:); labeled TCP latency test accurately (never mislabeled as ICMP ping).
- Radio & Signaling Previews: Marked non-operational radio lock controls and advanced L3 decoding strictly as "Advanced Pro — Preview Only".
- Help Center: Standardized placeholder to "Search Help topics...", aligned subtitle with Build 98 offline manual, and prevented category tab label crowding and truncation.

Signing status: Release AAB/APK remain unsigned pending authorized Google Play upload key. Do not publish to production until signed and approved.
