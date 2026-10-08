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

Reviewed offline catalogues are shipped in `resources/series-formats.json`
and `resources/movie-formats.json`. Technical formats come from explicit UK
Apple product-header badges, Stan title listings, and Dolby home-entertainment
case studies. Only confirmed fields are included: an Atmos article is not
evidence for HDR or resolution, and 5.1 does not identify an audio codec.
Every record has a source and check date; combined records retain evidence for
each added format. Public TVmaze and Cinemeta metadata match exact title/year
identities, rather than guessing from similar names. TVmaze identity links
provide attribution (https://www.tvmaze.com/api; CC BY-SA). No plots or artwork
are copied into these datasets.

These reviewed hints are immediately available on every device after an addon
update, even before playback or GitHub sync. Movie hints combine with the disc
catalogue, while actual source observations take priority, including an empty
or lower-quality result. Catalogue hints never assert that a specific source,
episode, language, region or subscription provides the listed formats.

The developer tools `tools/research-title-formats.py` and
`tools/research-stan-formats.py` cache public responses outside the addon,
extract only title-scoped badges, and reject uncertain identities. The Apple
parser excludes badges belonging to recommendations and trailers. These tools
are excluded from the installed package and never run inside Kodi. This
research makes no stream-addon requests. No bulk copy of the community disc
dataset is bundled or republished by this addon.

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
The old parallel browsing/account-maintenance stream scans remain disabled.
Opening a source picker still performs its normal source
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

## Optional slow discovery

Account & Stremio has **Slow background format discovery**, off by default.
It requires format sharing and the existing private GitHub sync token. It checks
movie/series titles with no known technical formats. One installed, enabled
AIOStreams addon is used per request, even if normal playback uses all addons.
The shared repository reserves one timestamp slot every three minutes using an
optimistic SHA write. Conflicts, malformed state, missing token or network failure
stop scanning. Multiple synced clients therefore compete for the same 20 hourly
slots rather than each spending 20. The slot file holds timestamps and bounded
hashed title keys to avoid duplicate attempts for 24 hours across devices. No raw
titles, URLs or credentials go in this file. Actual facts continue to use the
existing `formats.json` database and its five-minute sync.

Scanning now runs in the persistent service after three minutes of settled,
owned movie/episode playback. Browsing alone does not run source scans. Trailers,
pre-rolls, pauses, buffering, fast-forward and the final two minutes are excluded;
changing episodes restarts the settling period. It rechecks the local database
and foreground request budget immediately before a source request, records
complete successful observations, and retries unknown titles at most daily.
Provider errors/rate warnings impose a 30-minute shared backoff. A series uses
one representative episode, filters explicitly future-dated episodes, and
contributes to the high-level overview. Normal source searches defer local scans
according to their addon count and preserve any longer cooldown.
The scanner never sweeps every episode or restores the former parallel workers.

The local queue survives window closure/restart and holds up to 600 identities
for 30 days. Priority groups have separate bounds so a large watchlist cannot
evict all chart entries: Watchlist / Up Next (200), recently focused titles (150),
Popular / Trending (200), other loaded cards (50). Aliases and repeated lists
deduplicate by canonical identity. Known formats and explicit future releases
are skipped; the currently playing title is excluded.

One page from each configured movie/series Popular and Trending catalogue is
refreshed at most daily, using one supplier per chart/type and one page per tick.
These are catalogue requests, not stream searches, and still use their provider's
normal catalogue limits. A catalogue failure cannot block locally queued titles.
No complete catalogue or episode-library sweep is performed.

This consumes at most one third of a one-search-per-minute refill. It cannot measure
remaining server tokens, reserve tokens for other applications, or guarantee
against limits caused by other clients outside this sync repository.
Provider reference: https://docs.elfhosted.com/guides/media/hosted-jellyfin-frontends-and-rate-limits/

## Consistent presentation

Foreground learning reads/writes only affected facts; periodic shared merges
write only records that changed. Series overview queries use indexed ID ranges.
An unchanged sync does not rewrite the whole local catalogue. Streams supplied
directly in title metadata also contribute facts without extra addon searches.

Upcoming, Home, Discover and details heroes use the same high-level series
overview, including retained observations and the offline seed. Exact episode
source checks retain their original identity. IMDb-prefixed and explicit IMDb-ID
aliases read/write the same canonical facts. No name-only matching is used.

Blank duplicate posters reuse available artwork for the same type and canonical
ID. Poster image controls fall back to the original image or an independent
IMDb-based image endpoint if the configured server cannot load the image.
Provider-embedded quality badges are artwork, not evidence imported into the
technical database.
