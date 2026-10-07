# Provider and reliability pass — 1.8.18

## Configure providers

Open **Settings → Providers**. Preferences apply on this device and do not change your Stremio account's add-on configuration. Configured transport links are represented by hashes in the separate local preference file, so changing artwork preferences cannot overwrite a simultaneous watch-progress upload.

| Option | Behaviour |
| --- | --- |
| Title and episode details | Preferred metadata supplier first; other enabled suppliers fill missing fields, with Cinemeta as the final fallback. Reopen a title to fetch its merged details. |
| Posters and artwork | Preferred metadata supplier supplies posters across Home, Continue Watching, Up Next, Library, search and catalogues. Episode thumbnails prefer this supplier too. Automatic uses enabled AIOMetadata; missing posters retain original catalogue artwork. |
| Provider-supplied ratings | Prioritises actual supplied title/episode scores. Visibility switches remain under Ratings. Optional TMDB/MDbList enrichment remains separate, and series scores are never invented as episode scores. |
| Movie and series search | Preferred supplier is first in autocomplete and full-search duplicate resolution. Autocomplete requests the preferred supplier before Cinemeta; full search also includes other enabled searchable catalogues. Automatic preserves fast IMDb autocomplete. |
| Stream add-ons | All enabled stream add-ons, or just the chosen supplier. Source/quality/audio/video filters still apply to returned releases. |
| Subtitle add-ons | All enabled subtitle add-ons, or just the chosen supplier. Embedded tracks, inline stream subtitles, language rules and forced-subtitle safeguards remain available. |

Overlap entries explain available suppliers. Multiple metadata or search providers are not automatically a fault. Disabled/uninstalled preferences fall back automatically; they never reactivate a disabled add-on.

**Refresh artwork** invalidates only the configured poster-resolution cache by revision and refreshes the visible page after Settings closes. It preserves catalogue membership, progress and position. New posters load progressively; no metadata request is added per title to the startup path. The add-on cannot override a provider's own image cache or Kodi's cache when the provider reuses an unchanged image URL.

Configured preferences are kept in `<profile>/providers/account.json`; diagnostics in `<profile>/diagnostics/account.json`. These contain hashes/status summaries, not configured URLs. Existing private account storage remains unchanged.

## Disabled suppliers and background responses

Discover filters enabled descriptors, and rechecks stale selections before requesting items. Cached Home matches catalogue keys against current enabled descriptors, dropping disabled rows and restoring live pagination specs only in memory. Add-on changes invalidate old view caches. Artwork, lazy-page and hero responses check their generation before applying, preventing a previous page/provider from replacing the current one.

Search collapses equivalent IMDb IDs (`tt…` and `imdb:tt…`) while keeping movie and series types separate. Preferred-provider artwork wins duplicate resolution; results still require usable artwork and relevant movie/series titles. AIOMetadata custom poster styles are preserved, including integrated BetterPosters.

## Local troubleshooting and timing

Open **Settings → Troubleshooting** for:

- First app launch in the current Kodi session and repeat-launch median timings, with at most 12 saved samples.
- Background Home refresh duration, separate from time until usable Home.
- A network-free cached-browsing benchmark on the Kodi device.
- Current player appearance/ownership and the remaining live-player checklist.
- Latest supplier/resource status, cache versus network result, last network refresh, duration and fixed HTTP failure codes.

Request history is bounded to 48 entries. It excludes source links, configured manifest URLs, search text, title IDs and raw exception messages. It stays local and is not added to automatic feedback. Cached reads do not claim a fresh network update. Diagnostics cannot interrupt a request when their own storage fails.

The local Windows synthetic benchmark used 160 poster cache keys, one warm-up and seven samples. Median page read fell from **2230.36 ms** (previous per-item SQLite connections) to **17.53 ms** (one batch connection/trim). This measures cache work only, not cold Kodi boot, network latency or video loading. Real launch timings are recorded from the app's Python entry to Home initialization; Kodi's own boot time is excluded.

## Player checks

The audio/subtitle/settings pickers now cancel when their playing file changes or playback ends. Existing auto-hide, playback ownership, native-menu Back bindings and compact seek textures are retained. Automated tests cover lifecycle, audio/subtitle selection, finish-time stability, Back handling and XML navigation.

Actual device validation is still pending. The supplied device at `192.168.1.239:8080` could not be reached because it is on the user's home network while this PC is elsewhere. No playback or device settings were changed remotely.

On a reachable Kodi device, verify:

1. Open Audio, Subtitles and Settings during playing and paused video. Back returns to playback without a focus trap.
2. Stop playback or advance episode while a picker is open: the picker closes and never applies a choice to the new video.
3. Seek using remote directions and the slider. The handle stays compact and aligned to the line.
4. Resume and wait for the configured idle timeout: the controls hide. Paused/seek states keep the bar as intended.
5. Verify native adjustment dialogs, chapter controls, loading-screen dismissal and subtitle defaults, then confirm foreign playback/live TV keeps its native controls.

No release or public repository changes have been made for this pass.
