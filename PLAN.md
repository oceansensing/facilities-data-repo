# facilities-data-repo: the founding plan and running record

US **hospitals**, from USGS's National Structures Dataset and CMS. Created on GitHub by the owner and given its documents by the site's
`pipeline/scaffold/new-origin.py`. **Nothing is published yet.**

## What it is for

US hospitals: **`hospitals.json`**, every point of the National Structures Dataset's *Hospitals/Medical Centers* — its name, street address, city, state, ZIP and the day it was loaded — with, where the Centers for Medicare & Medicaid Services' *Hospital General Information* lists it, its phone, hospital type, whether it runs an emergency department and its facility id, and the join's own count by rule; and **`land/hospitals/`**, the same records as a pyramid of Mapbox vector tiles (uncompressed, extent 4096, one point layer `hospitals`), every hospital at every zoom from 4 to 10; its `index.json` names the version (the tiles' own hash) and every tile to zoom 8. R2's alone.

## Where the data comes from

**The places are the U.S. Geological Survey's**: The National Map's National Structures Dataset, `carto.nationalmap.gov/arcgis/rest/services/structures/MapServer/14` (6,550 points on 2026-10-20; the service's credit *"USGS TNM – National Structures Dataset"*; The National Map's data free and in the public domain, its credit *"Map services and data available from U.S. Geological Survey, National Geospatial Program"*). **What a hospital offers is CMS's**: *Hospital General Information*, data.cms.gov's provider data `xubh-q36u` (5,419 hospitals registered with Medicare; no license statement found on its page, its catalog's FAQ or its footer, so its use rests on its being a federal work, 17 U.S.C. § 105; its FAQ: no key, no rate limits). Its CSV's address changes with each release, so the catalog's record is read first. **The terms were read before a line was written** (2026-10-20).

## 2026-10-20: the first run, and the schedule

The first dispatched run (`39397796443`, 09:02-09:07 UTC) was green: the hospitals fresh - 6,550 of the National Structures Dataset's, 4,487 matched to Medicare's records - 5,487 tiles in `land/hospitals/`, R2's alone, the root on the `published` branch. The schedule set then: daily at 09:47 UTC, the step reading upstream each month.

## Open

1. A second run the next day: not due, the same version, nothing uploaded.
2. Then the daily schedule.
3. The join's rate read each month; the hospitals no rule finds, read by region.
