# Application Build & Integrity Verification

**Document ID:** `RFEX-LITE-BUILD-VERIFY-20261117-V1`  
**Product:** RFeX Drive Lite  
**Application ID:** `com.rfex.drive.lite`  
**Version Name:** `1.0.0`  
**Version Code:** `1`  
**Build Type:** `release`  
**Compilation Date:** November 17, 2026  
**Git Source Commit:** `a0b7bd6` (Branch: `review/lite-v1.0.0-build98`)  
**Gradle Tasks:** `bundleRelease assembleRelease testReleaseUnitTest` (61 tasks, 0 test failures)

---

## 1. SDK & Compiler Configuration

| Setting | Value | Verification |
| :--- | :--- | :--- |
| **Minimum SDK** | `26` (Android 8.0 Oreo) | Enforced in `build.gradle.kts` |
| **Compile SDK** | `36` (Android 16 Vanilla Ice Cream) | Enforced in `build.gradle.kts` |
| **Target SDK** | `36` (Android 16 Vanilla Ice Cream) | Enforced in `build.gradle.kts` |
| **Java / JVM Toolchain** | Java 17 (OpenJDK 17.0.12) | Target bytecode 17 |
| **Kotlin Compiler** | 2.0.21 | Target JVM 17 |
| **Android Gradle Plugin** | 8.7.2 | Standard stable release |

---

## 2. Release Artifact Cryptographic Hashes

Generated in:  
`D:\RFeX-Research\RFeX-Drive-Lite\Release-Candidate\RFeX_Drive_Lite_v1.0.0\Final-Public-Release\`

| Artifact | Size | SHA-256 Checksum | Signature Status |
| :--- | :---: | :--- | :---: |
| **`RFeX_Drive_Lite_v1.0.0_1_release_signed.aab`** | 8.84 MB | `7fb4a28c0bc3618f4705157fea691da773e2b2e9545be49ee78e456bd3d296ed` | Signed (`jarsigner`) |
| **`RFeX_Drive_Lite_v1.0.0_1_release_signed.apk`** | 4.60 MB | `7dce308c8d4894bc39bd3c6bdb32d37bab25d5db60ad9f1c417e70ffe9325542` | Signed (v1, v2, v3) |
| **`RFeX_Drive_Lite_v1.0.0_1_release_unsigned.aab`** | 8.84 MB | `0ce85fb7799ed88f472edffbd28672612f97b415c46c664ac191c2cd26d7df9e` | Raw Gradle output |
| **`RFeX_Drive_Lite_v1.0.0_1_release_unsigned.apk`** | 4.59 MB | `ebdc304b5587f96f22eeafee8394e15a4b80ae12364cfe6e4733e577ae578171` | Raw Gradle output |

---

## 3. Cryptographic Signature Verification

### Android App Bundle (AAB) Verification
```powershell
jarsigner -verify -verbose RFeX_Drive_Lite_v1.0.0_1_release_signed.aab
# Result: s = signature was verified, jar verified.
```

### Standalone APK Verification
```powershell
apksigner verify --verbose RFeX_Drive_Lite_v1.0.0_1_release_signed.apk
# Result:
# Verifies: true
# Verified using v1 scheme (JAR signing): true
# Verified using v2 scheme (APK Signature Scheme v2): true
# Verified using v3 scheme (APK Signature Scheme v3): true
# Number of signers: 1
# Signer: CN=RFeX Technology, OU=Mobile Engineering, O=RFeX, L=Hanoi, C=VN
```

---

## 4. Physical Test Device Environment
- **Device Hardware:** Xiaomi 13 Pro (`2210132G`, ADB serial `c0f1b48c`)
- **OS Platform:** Android 13 (MIUI 14 Global, build `TKQ1.221114.001`)
- **Baseband Modem:** Qualcomm Snapdragon X70 (`MPSS.DE.3.0-Aug 17 2023-21:01:42`)
- **Cellular Network:** Viettel 4G LTE (`PLMN 452/04`, Band 1, EARFCN 250, PCI 485)
- **Installation Verification:** Clean uninstallation of previous debug builds, succeeded with exit code 0 (`Success`).
