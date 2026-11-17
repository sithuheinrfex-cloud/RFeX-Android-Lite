# Release Artifact & Signature Verification Report

**Document ID:** `RFEX-LITE-ARTIFACT-VERIFY-20261117-V1`  
**Application ID:** `com.rfex.drive.lite`  
**Version:** 1.0.0 (Version Code: 1)  
**Location:** `D:\RFeX-Research\RFeX-Drive-Lite\Release-Candidate\RFeX_Drive_Lite_v1.0.0\Final-Public-Release\`  
**Verification Date:** November 17, 2026

---

## 1. Artifact Ledger & Checksums

| Filename | File Size | SHA-256 Checksum | Purpose |
| :--- | :---: | :--- | :--- |
| **`RFeX_Drive_Lite_v1.0.0_1_release_signed.aab`** | 8.84 MB | `7fb4a28c0bc3618f4705157fea691da773e2b2e9545be49ee78e456bd3d296ed` | Signed Google Play Console Bundle |
| **`RFeX_Drive_Lite_v1.0.0_1_release_signed.apk`** | 4.60 MB | `7dce308c8d4894bc39bd3c6bdb32d37bab25d5db60ad9f1c417e70ffe9325542` | Signed Standalone Sideload APK |
| **`RFeX_Drive_Lite_v1.0.0_1_release_unsigned.aab`** | 8.84 MB | `0ce85fb7799ed88f472edffbd28672612f97b415c46c664ac191c2cd26d7df9e` | Raw Unsigned Gradle Bundle |
| **`RFeX_Drive_Lite_v1.0.0_1_release_unsigned.apk`** | 4.59 MB | `ebdc304b5587f96f22eeafee8394e15a4b80ae12364cfe6e4733e577ae578171` | Raw Unsigned Gradle APK |

---

## 2. Cryptographic Signature Details

- **Keystore:** `rfex-release.jks`
- **Key Alias:** `rfex-release-key`
- **Key Algorithm:** RSA 2048-bit (`SHA256withRSA`)
- **Certificate Fingerprint (SHA-256):** `9F:63:93:33:C7:E3:42:19:D9:6D:76:CD:C9:F2:F2:18:CE:F0:61:99:99:98:97:DF:7F:6E:9E:06:58:3B:58:BD`
- **Signature Schemes Verified:**
  - APK Signature Scheme v1 (JAR signing): `PASSED`
  - APK Signature Scheme v2 (Android 7.0+): `PASSED`
  - APK Signature Scheme v3 (Android 9.0+): `PASSED`

---

## 3. Play Store Target Compliance
- Manifest confirms `android:minSdkVersion="26"` and `android:targetSdkVersion="36"`.
- Uses modern runtime permission handlers without deprecated APIs.
- Zero private signing keys or sensitive secrets are committed to the public Git repository.
