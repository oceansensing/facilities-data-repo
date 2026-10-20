# facilities-data-repo

US **hospitals**, from USGS's National Structures Dataset and CMS: a data repository of the oceansensing ocean map system, with its own
Pages site, its own schedule and its own gigabyte, and no code of its own.

**Publishing since 2026-10-20**, daily at 09:47 UTC, the step reading upstream each month. `PLAN.md` is the founding plan; `CLAUDE.md` carries what must not be
got wrong and the shared doc doctrine.

## What it publishes

US hospitals: **`hospitals.json`**, every point of the National Structures Dataset's *Hospitals/Medical Centers* — its name, street address, city, state, ZIP and the day it was loaded — with, where the Centers for Medicare & Medicaid Services' *Hospital General Information* lists it, its phone, hospital type, whether it runs an emergency department and its facility id, and the join's own count by rule; and **`land/hospitals/`**, the same records as a pyramid of Mapbox vector tiles (uncompressed, extent 4096, one point layer `hospitals`), every hospital at every zoom from 4 to 10; its `index.json` names the version (the tiles' own hash) and every tile to zoom 8. R2's alone.

These products are published **operationally but not drawn on the website's map**; the map's status
line still reports them when they fall behind, which is how their health stays visible.

## Where the data comes from

**The places are the U.S. Geological Survey's**: The National Map's National Structures Dataset, `carto.nationalmap.gov/arcgis/rest/services/structures/MapServer/14` (6,550 points on 2026-10-20; the service's credit *"USGS TNM – National Structures Dataset"*; The National Map's data free and in the public domain, its credit *"Map services and data available from U.S. Geological Survey, National Geospatial Program"*). **What a hospital offers is CMS's**: *Hospital General Information*, data.cms.gov's provider data `xubh-q36u` (5,419 hospitals registered with Medicare; no license statement found on its page, its catalog's FAQ or its footer, so its use rests on its being a federal work, 17 U.S.C. § 105; its FAQ: no key, no rate limits). Its CSV's address changes with each release, so the catalog's record is read first. **The terms were read before a line was written** (2026-10-20).

## How it runs

The orchestrator (the site's private `pipeline/`), the fetchers and the
published-file contract all come from `oceansensing.github.io`, checked out at
run time. This repository carries `pipeline/products.toml` and its publish
workflow, and nothing else executable. Each run publishes to GitHub Pages and
to Cloudflare R2 from one build. Related repositories: `aviation-data-repo` (the other land points, made the same way).

**Which document gets what, and what "update docs" means across all
thirty-one repositories, is the doctrine block at the top of `CLAUDE.md`**: the
same text in all thirty-one, held equal by the site's `check:docs`.

## Structure

```
README.md       what this is
CLAUDE.md       what must not be got wrong, and the shared doc doctrine
PLAN.md         the founding plan and running record
DECISIONS.md    dated one-way decisions, D1 onward
pipeline/       products.toml, the declaration the orchestrator reads
.github/        the publish workflow
```
