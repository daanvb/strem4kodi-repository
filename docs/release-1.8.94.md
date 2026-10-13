# Strem4Kodi 1.8.94

Hero quality logos now prefer the existing source-derived SQLite records and
private format sync. PostersPlus remains the poster artwork provider, and its
technical JSON facts fill missing resolution/HDR/audio families only. A known
source family cannot be upgraded by the fallback, and title-level fallback facts
cannot stand in for a selected episode. These fallback facts are not written to
the source-format database.

Focused source discovery is restored even when the artwork uses PostersPlus.
Fresh complete format records avoid both network paths. The removed page-wide
scanner and native poster sashes remain removed.

Media page loading messages are cleared on successful completion. Errors and
other operation messages are retained. The background format-check label is
removed from that page; actual source search and playback errors stay visible.

Player skin remains 0.1.23. Restart Kodi after updating.

Low-power follow-up: fast focus changes share a saved-progress read for up to
500 ms, while a progress signal or changed spoiler setting forces an immediate
refresh. Browsing no longer fetches director facts for removed native poster
tags. Repeated selection events are guarded for 250 ms across media-loading
transitions; Back, Cancel and directional actions remain immediate.

Episode progress uses the native ListItem.PercentPlayed value backed by the
item's resume point, including refreshed partial progress after playback.
Missing saved duration may use that exact episode's runtime. The one-millisecond
next-episode pointer, invalid numeric values and watched episodes do not create
partial bars. Current measured duration remains the most accurate runtime;
validated TMDB episode runtimes replace provider estimates when configured.
This invalidates old season-enrichment records that omitted the runtime field.

These changes have no measured Toshiba Fire TV speed or rendering result yet;
automated correctness checks are separate from the device retest.

Recommendation follow-up: title-detail Similar cards use the same configured
artwork resolver/cache as Home and Search. Fresh artwork updates only matching
cards and is cancelled when the section changes or the window closes. Native
window closure shares the artwork update lock; no HTTP request holds that lock.

You May Also Like uses up to five watched, in-progress or saved taste seeds.
TMDB recommendation results lead; weekly trending charts supply additional
genre-matched choices. Ordinary candidates require at least 7/10 and 100 votes.
Trending requires stronger genre overlap, and animation/documentary seeds keep
those categories. Existing exact collection sequels remain eligible.
Titles already saved, continuing or completed are removed by canonical IDs both
before ranking and while reading caches. External-ID lookups remain capped at
ten, charts are fetched once per kind, and generation stays off the Home thread.
Versioned caches and snapshot markers retire the earlier weak recommendations.

Poster focus frames are expanded into the surrounding gutter, keeping their
stroke outside the artwork and its top-edge chips. This applies to generated
normal/compact poster lists and the title-detail Similar cards. The poster
image, chip placement and progress geometry remain unchanged.

Artwork ordering follow-up: AIOmetadata resolves first before other metadata
providers. Trusted AIOmetadata catalogue artwork may display immediately; other
movie/series artwork is held behind neutral placeholders pending its response.
Backgrounds, landscape cards and logos share this rule, including Favourites and
Watch Later. Provider provenance and a new artwork generation retire older cache
records that did not validate these fields. Source failures allow fallback art
without replacing an already verified image from the same configuration.

Clearing all response caches, metadata/catalogue/search, or Refresh artwork
also invalidates artwork choices and startup snapshots. Kodi textures are removed
only for exact URLs recorded as Strem4Kodi artwork. Persistent cache generations
reject pre-clear workers and isolate hot memory entries across Kodi scripts.
Saved lists, sign-in, progress and shared source-format records are preserved.
Kodi RPC failure is reported as incomplete, not success. AIOmetadata/PostersPlus
server-side caches remain managed separately. These checks simulate Kodi API
responses; physical-device rendering still needs a retest.

Trailer focus follow-up: returning an owned trailer from Kodi fullscreen uses
ActivateWindowAndFocus with the control and position captured immediately before
playback. Home and title XML now allow Kodi to remember focus on window return,
rather than always forcing the sidebar or Play button. Initial startup still
uses the explicit first-load focus path. Recovery remains scoped to the owned
trailer, its originating window and no active modal dialog. No per-tick focus
forcing is added, so intentional navigation remains unaffected.

Release validation (13 October 2026): the integrated source passed all 1,581
automated regression tests using the bundled Windows interpreter and Pillow
12.3.0. The final Home template/generated-layout check also passed after
aligning the template utility. Source credential scanning, package/source
agreement, Python/XML compilation, ZIP integrity and staged-feed checks passed.
No physical Fire TV or Shield retest is claimed by these automated checks.
