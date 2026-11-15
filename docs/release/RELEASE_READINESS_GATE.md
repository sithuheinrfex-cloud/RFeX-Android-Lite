# RFeX Drive Lite v1.0.0 — Public Release Review Gate

**Status:** NOT RELEASE APPROVED — review and reconciliation required  
**Repository:** `sithuheinrfex-cloud/RFeX-Android-Lite`  
**Review branch:** `review/lite-v1.0.0-public-release`  
**Package:** `com.rfex.drive.lite`  
**Planned version:** `1.0.0` / versionCode `1` (verify against Play Console before submission)  
**Review established:** 2026-11-15

This branch currently contains governance/review instructions only. The actual latest Lite working tree, release-candidate source, full help/manual/datasheet, build outputs, and Xiaomi evidence have **not** been independently examined in this GitHub branch. Never call these checks PASS until local source and resulting compiled artifacts are inspected.

## 1. Scope freeze

Ship an Android public-SDK-only RFeX Drive Lite app. Retain RF measurements, available serving/neighbor-cell data, network events, route/GNSS recording, map and supported exports, and the professional Lite-safe UI.

Speed Test:
- Cloudflare Speedtest: reviewed MIT-licensed `@cloudflare/speedtest` library, default intended UX, **public hosted-endpoint enablement BLOCKED until service rights/conditions resolved**. Its default autoStart must be overridden to false. If blocked in production, do not expose a default mode with a dead Start button: use the working, authorized OpenSpeedTest option instead, and disclose functionality accurately.
- OpenSpeedTest Public: official hosted iframe `https://openspeedtest.com/speedtest`, user-initiated, widget results stay in the widget. Credit visible as “Powered by OpenSpeedTest” with link.
- LibreSpeed: **DEFERRED / NOT SHIPPED**. Remove its release runtime dependencies, settings, manifest entries, user-visible options and release claims. Development-only source may remain separately, outside the Lite release module and artifact.

Do not ship root, Magisk, Qualcomm DIAG/QMDL, AT, RRC/NAS/L3 decoders, Pycrate, band/cell/ARFCN/PCI locking, PCTEL scanner integration, privileged radio control, QA FULL flags or enterprise-only code. It is acceptable to show read-only, accurately labeled tier descriptions without active controls.

## 2. Mandatory audit matrix (record PASS / FAIL / BLOCKED and evidence)

| Gate | Required evidence | Status |
| --- | --- | --- |
| Source identity | Actual source ref, working-tree diff and module inventory | PENDING |
| Scope exclusion | Runtime dependency graph, merged manifest, final AAB/APK inspections and grep of forbidden APIs | PENDING |
| Android compatibility | targetSdk >= 36; minSdk/device compatibility; runtime permission flow; Android 13/14/16 checks | PENDING |
| Map | Actual basemap features on Xiaomi, panning/zoom, GNSS-independent render, provider attribution, tiles policy | PENDING (prior failure) |
| Cell/RF/GNSS | Real API values; precise location toggle; dual-SIM; no fabricated measurements; recording and route export | PENDING |
| Events / Band UI | Professional Build 98-inspired appearance, Lite-only capabilities, no false root/DIAG statuses | PENDING |
| Cloudflare QA | Reconcile reported device evidence (331.2/98.2 Mbps; 43.3ms latency; 7.7ms jitter) | REPORTED PASS — VERIFY |
| OpenSpeedTest QA | Reconcile reported device evidence (391.8/56.5 Mbps; 51ms ping; 1ms jitter) | REPORTED PASS — VERIFY |
| Cloudflare endpoint permission | Written/vendor policy confirmation or supported usage evidence for shipped Android app | BLOCKED |
| Third-party inventory | Exact direct/transitive dependency list, pinned versions, license IDs, copyright notices, notices bundled in app | PENDING |
| Privacy & Play Data safety | Network data flow, map/measurement server traffic, permissions, user notices, site privacy URL, declarations reconciled | PENDING |
| Play listing/assets | App name/package, logo and screenshots, truthful feature claims, content rating and app-access declarations | PENDING |
| Native library compatibility | 16 KB page-size compliance for any native libraries in shipped AAB | PENDING |
| Security | Release manifest, TLS, WebView sandbox, secrets scan, exported components, local storage, dependency vulnerability review | PENDING |
| Performance | Crashes/ANRs, battery/thermal, speed-test cancellation, no auto/background data traffic, memory | PENDING |
| User documents | Offline Help, manual, datasheet, privacy, OSS notices, release notes consistent with actual release | PENDING |
| Build and signatures | Fresh reproducible release AAB/APK; approved secure upload signing; package/version/dex/deps/sha256 checks | PENDING |
| Publication | Owner approval after review; Play Console tests and policy declarations | NOT AUTHORIZED |

## 3. Required third-party compliance actions

- **RFeX product license:** Determine the owner-selected license for first-party code. An MIT dependency does *not* force the overall RFeX codebase to be MIT or open source. Never silently add a root LICENSE granting public reuse.
- **Cloudflare:** Keep the complete MIT copyright/license text with the shipped library; review the README's Cloudflare collection of completed measurement results; independently check Cloudflare hosted measurement-service terms. Source-code MIT permission must not be presented as guaranteed unlimited Cloudflare server use.
- **OpenSpeedTest:** Source of the hosted widget and embed rights: https://openspeedtest.com/selfhosted-speedtest#Embed-SpeedTest . Preserve vendor branding/link; avoid scraping widget results or inventing integrated RF metrics; verify provider privacy disclosure and the actual iframe behavior.
- **Map data/SDK:** Identify the *actual* shipped mapping SDK (MapLibre vs osmdroid vs other) from source and final bundle. Inventory its license plus each map/tile provider. Display “© OpenStreetMap contributors” when appropriate and follow the tile provider's caching, User-Agent, HTTPS and no-bulk-fetch rules. See https://operations.osmfoundation.org/policies/tiles/ .
- **Other libraries:** Enumerate Compose/AndroidX/OkHttp/etc. from actual resolved release configuration; include their exact notices per license. Do not guess which versions are shipped.
- **No false endorsements:** “Powered by …” and “Map data © …” credits must not imply Cloudflare, OSM or OpenSpeedTest endorses RFeX.

## 4. Documentation deliverables

Review actual files and synchronize all feature statements before publication:
1. Product datasheet — Lite-supported functions, hardware/API limitations, Lite vs Pro vs Advanced Pro, no active root/DIAG/locking, truthful speed-test capabilities.
2. Offline Help — permission troubleshooting, GNSS/Location Master/Precise, map and offline behavior, network/data consumption, user-initiated speed test, server/privacy notices, help links.
3. Full manual — supported workflows for cellular readings, dual-SIM, observations, recording, map layers, file import/export (only if implemented), error states, data retention, limitations.
4. Privacy policy — RFeX device/location data collection and storage, user-controlled exports, Cloudflare/OpenSpeedTest/map traffic, vendor policies, support/privacy contact; hosted publicly at an HTTPS URL and linked in-app.
5. Open-source notices — complete license text where required; direct and transitive libraries verified; visible OSM and OpenSpeedTest credit; no LibreSpeed claim if excluded.
6. Play listing — short/full descriptions, truthful feature matrix, screenshots from actual Lite build, developer contact, privacy URL, Data safety, ads declaration, app access, content rating, target audience, release notes.
7. Release record — signed SHA-256 manifest, exact Gradle revision, source SHA, tested APK/AAB identity, version and signing identities, device evidence, PASS/FAIL/BLOCKED table.

## 5. Git protocol for the local candidate

1. Work only in the isolated Lite workspace (not the original Build 98 QA/Pro workspace).
2. Record `git status --short`, `git branch -vv`, `git remote -v`, `git log -5 --oneline`, and compare local changes with the remote review branch before editing.
3. Preserve all uncommitted local work and do a reversible backup/worktree before any branch switch, rebase, reset, copy, or merge. This public GitHub repository is documentation-first and must not be treated as permission to open-source the proprietary Build 98-derived Lite code.
4. Audit and fix the real candidate locally, run target tests, then commit **reviewed public documentation, sanitized screenshots, public example data and legal notices only** to this public release-review branch, with narrowly scoped commits and clear messages. Keep Android Kotlin/Java source, build tooling, internal test evidence and release binaries in the private/local engineering workspace unless the owner separately approves the source-code license and public IP disclosure.
5. Never commit keystores, passwords, tokens, production certificates, private customer data, device logs exposing identifiers, unsigned or debug APKs/AABs, local SDK settings, QA/Pro restricted code, or unlicensed proprietary assets.
6. Verify upstream branch and any remote publication step separately from local commit; **no merge to main, tag, GitHub Release, VPS deployment, Play upload or production rollout** without specific owner approval.
7. Add a final, evidence-backed PASS/FAIL/BLOCKED review summary before requesting release approval.

## 6. Current official policy sources (recheck at the end of audit)

- Google Play target SDK API 36 from Aug 31, 2026: https://support.google.com/googleplay/android-developer/answer/11926878
- Google Play user data and Data safety: https://support.google.com/googleplay/android-developer/answer/10144311
- Google Play app signing: https://developer.android.com/studio/publish/app-signing
- Android 16 KB page sizes: https://developer.android.com/guide/practices/page-sizes
- OSM raster tile use: https://operations.osmfoundation.org/policies/tiles/
- Cloudflare library license/source: https://github.com/cloudflare/speedtest
- OpenSpeedTest official hosted embed: https://openspeedtest.com/selfhosted-speedtest#Embed-SpeedTest
