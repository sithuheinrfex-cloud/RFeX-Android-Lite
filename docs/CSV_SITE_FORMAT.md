# CSV Site Database — RFeX Drive Lite

**Draft input contract, to be matched to actual parser tests before release.** Lite imports CSV only.

## Minimum and optional fields

| Field | Required? | Meaning / format |
|---|---|---|
| `site_id` | Yes | Stable site identifier; repeated sector rows share the same ID |
| `latitude` | Yes | Decimal WGS84 degrees from -90 to +90 |
| `longitude` | Yes | Decimal WGS84 degrees from -180 to +180 |
| `site_name` | Optional | Human-friendly name |
| `sector_id` | Optional | Real sector identifier, unique per site where possible |
| `technology` | Optional | LTE, NR, WCDMA, GSM, etc. as data labels only |
| `azimuth_deg` | Optional | Physical antenna bearing 0 to <360 degrees |
| `beamwidth_deg` | Optional | Positive antenna beamwidth <=360 degrees |

The actual importer may support additional headers or aliases if explicitly tested. Do not advertise unimplemented aliases. Do not assume omitted antenna height, tilt or power values.

## Example CSV

```csv
site_id,site_name,latitude,longitude,sector_id,technology,azimuth_deg,beamwidth_deg
YGN00001,Sample Site A,16.8409,96.1735,A,LTE,0,65
YGN00001,Sample Site A,16.8409,96.1735,B,LTE,120,65
YGN00001,Sample Site A,16.8409,96.1735,C,LTE,240,65
YGN00002,Sample Site B,16.8661,96.1951,A,NR,90,65
```

This is **synthetic CSV for parser testing only**. It is not a real site inventory or an RF prediction.

## Free limits and validation

- Count **unique `site_id` values** with valid coordinate pairs; don't count each repeated sector row as another site.
- Limit to **100 sites** at a time. For a file with 101+, present an explicit subset-selection workflow before import, with no silent truncation the extras.
- Show all selected **Site Points** on map and preview **up to 3 selected sites** with valid sector geometry. Site points without sector azimuth remain points.
- Import safely using Android Storage Access Framework; read-only input access, size/row safeguards, CSV quotation/escaping, UTF-8 handling, and coordinate validation.
- Invalid coordinates, duplicate IDs with conflicting positions, missing IDs, misleading sector azimuth/beamwidth and non-CSV formats should result in descriptive errors or explicit review.
- **Not supported:** KML, KMZ, XML, MIF/TAB or arbitrary spreadsheet formats.
