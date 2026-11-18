# Open-Source and Hosted-Service Licensing

RFeX Drive Lite's first-party code is **proprietary freeware**; permissive third-party licenses do not require that proprietary source be public.

Upstream licenses independently checked:
- **osmdroid:** Apache-2.0 — https://github.com/osmdroid/osmdroid/blob/master/LICENSE
- **OpenSpeedTest code:** MIT — https://github.com/openspeedtest/Speed-Test/blob/main/License.md
- **OpenStreetMap data:** ODbL — https://www.openstreetmap.org/copyright
- **AndroidX/Kotlin dependencies:** obtain exact license/NOTICE data for each library actually distributed.

**Separate service permissions:** OpenSpeedTest publicly offers hosted-widget embedding for personal and commercial use with provider attribution: https://openspeedtest.com/selfhosted-speedtest . OpenStreetMap tile servers have strict usage policies independent of database ODbL: https://operations.osmfoundation.org/policies/tiles/ . Unofficial Google map-tile URL access is not permitted: https://developers.google.com/maps/faq .

Check the final compiled AAB/APK for all direct/transitive dependencies. A historical SBOM listed LibreSpeed/LGPL despite a separate report saying it was excluded; inspect the real artifact, and meet all applicable LGPL obligations if included. Removing a contradictory SBOM from public documents **does not waive licensing obligations**.

See [third-party notices](../../THIRD_PARTY_NOTICES.txt) and [license verification](../release/LICENSE_VERIFICATION.md).
