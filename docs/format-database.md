# Shared format database

Browsing logos are a high-level guide to known picture and audio formats. They
are not a guarantee that every episode, language or currently available stream
has those formats. The selected stream and Kodi's detected playback information
remain authoritative in the player.

## Free sources and local lookups

Each device downloads the existing community disc catalogue at most weekly:
https://github.com/Appz4Fun/fel-dolby-vision-movies

The explicit `hdr_formats` and `audio_formats` fields supply movie release
hints. Resolution is added only for an explicit 4K Blu-ray release link; FEL
membership alone is not used to guess audio or HDR. The live catalogue import
was checked on 8 October 2026: 1,177 release rows supplied 1,163 distinct movie
format records. Coverage is limited and is not a general TV format database.

A small offline series seed is shipped in `resources/series-formats.json`. The
48 reviewed entries include 42 Apple TV series with hero badges verified from
UK title pages (4K, Dolby Vision and Atmos), plus six series with formats
explicitly confirmed by Dolby. Only confirmed fields are included: an Atmos
article is not evidence for HDR or resolution. Every entry has a source and
review date. The expanded entries use TVmaze only to match series identities,
with per-entry identity links for attribution (https://www.tvmaze.com/api);
technical formats come from the linked Apple or Dolby pages. This is a starter
catalogue, not coverage of all streaming TV.
It is available immediately on every device, even before playback or GitHub
sync. Addon updates distribute reviewed seed changes. The developer tool
`tools/refresh-series-formats.py` can refresh the Apple entries; it reads only
hero badges before episode links and never runs inside Kodi.
No bulk copy of the upstream dataset is bundled or republished by this addon.

The device keeps a local SQLite database in its Kodi profile. Reading logos
does not search stream add-ons. The existing catalogue download populates the
database at startup; a new device needs that first successful download. Known
records subsequently work offline. Failed catalogue updates preserve existing
data. The focused hero polls its local badge state, so incoming facts can
appear without restarting a trailer or moving away and back.

Actual source lookups made when opening titles or selecting sources also save
neutral format facts. Complete results override disc hints, including quality
downgrades. Failed or partial provider replies cannot overwrite complete shared
facts. Source observations remain available indefinitely, with their original check
date. They may be refreshed after an hour when a title is explicitly opened,
subject to the existing shared request
budget and rate-limit cooldown. A series overview combines the shipped catalogue and a shared record of formats
observed across the series. A later low-quality episode result does not erase
known higher formats from the overview, even if it replaces the last result
for that same episode. Exact episode/source results still take priority in the
player. The series hero keeps the broader overview even if its next episode has
only lower-quality sources.
There is no automatic per-episode scan to populate that overview.

## Multiple devices

In Settings > Account & Stremio, **Share format database between devices** uses
the existing private GitHub sync repository and **Private GitHub sync token**.
Put a token with access to the same private `daanvb/strem4kodi-sync` repository
on every device. This option defaults on but transfers nothing without a token.
No additional subscription or metadata API signup is required. Without the
token, local disc hints and observations still work independently.

`formats.json` contains only canonical IMDb movie/episode/series IDs, whitelisted
format tags, observation dates and completeness flags. It contains no playable
URLs, provider configuration, account credentials or watch-progress fields.
The IDs do reveal which titles have format observations, so sharing is confined
to the private repository. Public repositories are rejected.

Devices pull and merge at startup and every five minutes. A GitHub write occurs
only when the merged contents differ from the remote file, at most once per
cycle per device. Source lookups save locally immediately; sharing is batched. GitHub updates use
the current file SHA, then read back to verify the upload. Concurrent changes
retry on the next cycle; newer local observations cannot be replaced by an
older device. There is no age expiry or 1,000-record cutoff. The shared JSON file has an
800 KiB safety limit, below the GitHub inline-file boundary; reaching it pauses
uploads with a status message and preserves all local facts rather than pruning
the catalogue. Existing pre-database local availability summaries are imported
once when sync runs, with their original dates.
Disc catalogue facts are downloaded separately and are not reuploaded.

See **Format database sync** in Account & Stremio for the current sharing status.
Browsing background stream scans, including the old account-maintenance source
prefetch, are disabled. Opening a source picker still performs its normal source
lookup; the database does not replace playable stream discovery.

Unknown titles remain without logos until technical information is available.
This improves lookup speed and cross-device reuse, but cannot promise universal
coverage or a two-second first-time live provider response.

## Capability identifiers and source combinations

Format IDs are stable identifiers, not quality rankings. Current mapping:

| ID | Capability |
|---|---|
| 0 | 4K |
| 1 | 1080p |
| 2 | 720p |
| 3 | 480p |
| 4 | 360p |
| 5 | Dolby Vision |
| 6 | HDR10+ |
| 7 | HDR10 |
| 8 | HDR |
| 9 | Atmos |
| 10 | TrueHD |
| 11 | DTS-HD MA |
| 12 | Dolby Digital Plus |
| 13 | DTS |
| 14 | Dolby Digital |

Never renumber these IDs; append future capabilities. Each complete source
lookup stores distinct anonymous capability combinations in `sources`, alongside
the title's readable format summary and observation date. Atmos remains separate
from the underlying audio codec. Duplicate combinations are combined; no source
URL, filename, provider identity or access token is stored. These are source-level
reported capabilities, not a guarantee about which individual audio track is selected.

Old cached summaries, reviewed series entries and disc facts remain valid inputs.
Old summaries cannot reconstruct individual source combinations; those are learned
on subsequent normal source lookups. Verified series facts ship with the addon;
disc facts use the separate public download and are not republished to private sync.
The hero summarises known capabilities; it does not claim every combination exists
in one stream. Source cards and playback use their own stream information.
