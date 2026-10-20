# Decisions

Dated, irreversible-leaning decisions, one entry each, newest last. The
reasoning lives in `PLAN.md`.

**What counts as one-way in a data repository**: a decision that puts bytes in
readers' hands under a shape they will code against; a decision about which
repository owns a product, since moving one costs a migration in two places;
and a decision that forecloses an upstream.

## D1 — 2026-10-20 — Its own repository, R2 alone, its tiles made from its root every run

US hospitals get a repository of their own (2026-10-20), the first of the places a rescue needs, and **publish to Cloudflare R2 alone**, as every new product since the site pipeline's D13: Pages carries the status alone, and the website's map draws nothing of it. The records are the root, banked on the `published` branch; the tile pyramid beside it is made from them on every run, since a folder is never banked, and the sources are read monthly.
