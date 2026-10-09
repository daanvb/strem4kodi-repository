# Earlier release highlights

Historical behaviour below describes those releases; use the configuration guide for current setup.

## What's new in 1.8.49

- Tighter settings with ten visible rows, a smaller help panel and the native scrollbar.
- Readable subtitle and provider values; press Info for the full value and description.
- Improved duplicate-title merging and sharing of missing artwork/details across catalogue lists and pages.
- Blank posters display an independent fallback. No extra stream searches or provider tokens are used by these fixes.

Player skin remains **0.1.14**. Restart Kodi after updating.

## What's new in 1.8.48

- Clearer settings with visible overflow arrows, compact help and focus that stays on the option you changed.
- Fixed blank Credits start confirmations; the notification shows the saved time.
- Up Next sits lower/right and keeps **Loading…** visible until the next episode begins. Skip Outro yields while its card is open.
- An offline catalogue of **249 reviewed movies and 172 series**, alongside retained source and disc observations.
- Optional **Account & Stremio > Slow background format discovery** remains off by default. When enabled with private format sharing, it waits three minutes into stable playback, then checks at most one missing title every three minutes across linked devices. Prioritises saved and recently browsed titles, then Popular / Trending; pauses for buffering, trailers, browsing and episode endings, with shared daily duplicate protection and error backoff. Other apps share your provider allowance.

Player skin remains **0.1.14**. Restart Kodi after updating.

## What's new in 1.8.47

- Faster learned-format database updates and consistent series logos across browsing screens.
- Poster fallbacks and shared artwork for blank duplicate titles.
- An offline catalogue of 88 verified series, plus retained source and disc observations.
- Optional **Account & Stremio > Slow background format discovery**. Off by default; AIOStreams only, one request every five minutes across devices using the same private sync repository. Pauses during trailers/playback and backs off on errors.
- More room for troubleshooting descriptions, without scrolling.

Includes the Popcornmeter and rating-award improvements from recent updates. Player skin remains **0.1.14**. Restart Kodi after updating.

## What's new in 1.8.40

- Show explicit catalogue quality/audio fields immediately on hero focus, with cached source formats taking precedence and no stream searches while browsing.
- Add a persistent shared request budget for automatic title-opening checks: one minute per stream addon plus an extra minute between checks.
- Pause automatic title checks for at least 15 minutes after failures. Manual source selection and refresh remain available.
- Keep automatic whole-page stream searching disabled for all addons.

Player skin remains at **0.1.14**. Restart Kodi after updating.

## What's new in 1.8.39

- Disable automatic background stream searches for every addon, reserving requests for explicit title opening, source selection and playback.
- Stop whole-page format scanning while retaining cached logos and normal catalogue/artwork loading.
- Opening details still checks the movie or relevant episode and reuses fresh cached sources.

Player skin remains at **0.1.14**. Restart Kodi after updating.

## What's new in 1.8.38

- Reserve public AIOStreams searches for deliberate title opening, source selection and playback. Skip background logo searches against its public and development instances.
- Keep cached format badges while browsing; opening details checks the movie or relevant episode and reuses fresh source results.
- Avoid repeating a detail-page prefetch for an episode already checked during that visit.

Player skin remains at **0.1.14**. Restart Kodi after updating.

## What's new in 1.8.37

- Faster background logo checks use independent addon queues so slow providers do not block every row. Retain known logos during refresh and add local loading diagnostics.
- Optional movie audio pre-rolls match the selected source, with configurable Dolby Digital fallback or no pre-roll for DTS. Press OK to reveal Skip pre-roll, then OK to continue.
- Refresh the public GitHub pre-roll catalogue hourly, retaining the last successful catalogue offline and respecting additions and removals.
- Add Troubleshooting > Play FEL7 test video using the original Kodi-linked V4 test pattern, with GitHub test assets preferred when available.

Player skin remains at **0.1.14**. Restart Kodi after updating.

## What's new in 1.8.36

- Faster series format/logo searches reuse known episodes and avoid unnecessary full metadata merges.
- Full title details keep their existing metadata behaviour.

Player skin remains at **0.1.14**. Restart Kodi after updating.

## What's new in 1.8.35

- Background format checks keep scanning loaded rows, continue during trailers and retry failed requests.
- Faster addons can supply badges before slower results finish.
- Movie and episode clocks account for saved progress; the action menu is narrower.

Player skin remains at **0.1.14**. Restart Kodi after updating.

## What's new in 1.8.34

- Format availability loads across every loaded row, with known badges retained during background refresh.
- Scrub and chapter clocks follow playback until you select a position.
- A cleaner clock icon, more compact action menu and corrected Resume focus styling.

Player skin remains at **0.1.14**. Restart Kodi after updating.

## What's new in 1.8.33

- Display-sized transparent logos preserve colour artwork and reduce runtime scaling.
- Page-load availability checks prepare badges for the first eight titles before playback.
- Scrub and chapter transitions no longer reveal the underlying player menu; Down opens the player controls.
- Movie heroes show a small clock and estimated finish time beside the genre.

Includes **Player skin 0.1.14**. Restart Kodi after updating.

## What's new in 1.8.32

- Smaller transparent format logos sit at the hero's lower right, above the title rows.
- Unwatched focused titles can check availability before playback, including during hero previews.
- Player overlays blend into the picture; chapter and scrub panels fade smoothly.
- Common foreign chapter labels translate to English locally, without sending text online.

Includes **Player skin 0.1.13**. Restart Kodi after updating.

## What's new in 1.8.31

- Transparent format logos sit beside the genre and blend into Media info.
- Focused titles check source availability in the background before opening details.
- Cast filmographies open correctly; section menus and episode progress spacing fit better.
- Player timelines use a filled track and clear white marker. Feedback without buttons is more compact, with an OK hint for controls.

Includes **Player skin 0.1.12**. Restart Kodi after updating.

## What's new in 1.8.30

- Upcoming uses the same UK age certificates as other browsing rows, while retaining episode release information.
- Cast and crew profiles open a deduplicated filmography, newest first. Requires your TMDB API key.
- Compact format logos show fresh source-reported availability for the exact movie or episode. Player Media info follows detected playback and the selected audio track.
- Matching Dolby, DTS and HDR badges, tighter runtime spacing, and a simpler details menu without Languages.
- Player timelines align across modes, episode synopsis previews replace series plots, action labels fit, and automatic text scrolling is disabled.
- Episode progress has a clearer track and percentage.

Includes **Player skin 0.1.11**. Restart Kodi after updating. Actual TV rendering remains to be checked on your device.

## What's new in 1.8.29

- Scrub and chapter timelines share one clean panel, proper arrow graphics and aligned remote guidance.
- The episode synopsis blends into the lower player controls in a compact two-line block.
- Stop playback is removed from Settings. The episode range action now reads **Mark all episodes watched to here**.
- Resolution, HDR and detected audio use matching badge tiles. HDR10+ is supported; video codec badges are removed.

Includes **Player skin 0.1.10**. Restart Kodi after updating. Actual Shield rendering remains to be checked on your device.

## What's new in 1.8.28

- Player Settings puts **Chapters**, **ChaptersDB** and **Smart credits** first, without repeating the dedicated Audio, Subtitles and Media Info buttons.
- Scrubbing uses a solid panel with a clear time preview, chapter markers and two short help lines, covering the underlying controls.
- A floating episode title and synopsis appears while the player controls are open. The details hero retains a small eight-pixel gap between episode title and description.
- Sharper original Dolby Vision, TrueHD and Digital Plus logos retain their proportions and readable contrast. Atmos keeps the original Dolby artwork.

Includes **Player skin 0.1.9**. Restart Kodi after updating. Actual scene preview thumbnails are not included in this release.

## What's new in 1.8.27

- **Discover** uses vertical grids consistently, retaining Home-sized posters and the hero. Clipped captions are hidden and Up no longer enters the sidebar from a list.
- **Scrubbing** accelerates more gradually, shows clear preview feedback and offers seek-on-release or press-OK confirmation.
- **Credits start** is a small round player button that records manual smart-credit samples. Correct or delete samples and sync changes privately between devices.
- Episodes count as watched after **85% actual viewing**, either credits card appearing, or pressing Credits start. Movie rules are unchanged.
- **Use ChaptersDB instead** lets you choose an online edition and chapter list even when embedded chapters exist.
- Selected audio badges refresh consistently. App branding is transparent and the loading screen says **Bear With...**. AI subtitle translation has been removed; normal and forced subtitles remain.

Update the companion player skin to **0.1.8** and restart Kodi after updating. Remote navigation and rendering still need checking on your device.

## What's new in 1.8.25

- **My Lists** separates My Watchlist and My Favourites, with add, move and remove actions. A title can belong to both. Stremio retains the shared saves and progress; optional private GitHub sync shares the classifications between devices.
- Choose your **Discover opening list** under Settings > General.
- Single-episode watched/unwatched changes now share consistent episode ordering, support specials and verify the saved state.
- Media Info adds **720p HD, 1080p Full HD, 4K UHD and 8K UHD** badges and the underlying Dolby format alongside detected Atmos.
- Loading Video now says **Bear With**. Unreadable embedded chapter times fall back to ChaptersDB when enabled, with manual edition selection before jumping.

Restart Kodi after updating. Enable **Sync favourites and watchlist tags** under Account & Stremio on each device and use the existing **Private GitHub sync token** under API keys. Companion player skin **0.1.6** remains current.

## What's new in 1.8.24

- Resume tries the last successful source for that movie or episode before normal ranking, respecting filters and the quality ceiling. Manual source selection stays manual.
- Sports uses wide thumbnails automatically across catalogue pages and saved sports rows.
- Press **OK → Up → Up** for chapter timeline selection, or open **Settings → Chapters** for a chapter list with start times. Up before opening the controls no longer causes a large forward jump in the custom player.
- Player idle hiding now handles modeless controls. Hero trailers stay windowed, Discover captions no longer clip beneath posters, and single episodes always offer a **Mark unwatched** action.

Restart Kodi after updating. Companion player skin **0.1.6** remains current.

## What's new in 1.8.23

- The main sidebar has more clearance from posters, dims browsing content and only highlights a poster when its row has focus.
- Episode actions clearly distinguish **Mark this episode watched/unwatched** from **Mark all up to here watched/unwatched**. Unwatched thumbnails follow your spoiler setting immediately.
- Preferred posters survive progress refreshes and expired caches; older requests cannot overwrite newer artwork.
- Player **Media info** shows detected video/audio details, with Dolby Vision details when Kodi exposes them. Provider claims are labelled separately.
- A taller seek bar and clearer chapter markers support **Up** for scrubbing, then **Up** again for chapter selection; preview with Left/Right, jump with OK and return to scrubbing with Down.
- Player controls hide after inactivity even when a stale seek overlay remains; pause, buffering and open adjustment menus retain controls.
- Chapter edition matching uses available runtime and release clues without automatically selecting an uncertain edition.
- Long-press a card for **Artwork details**, including provider/cache selection and episode blur explanations.
- Movies and Series remember separate Discover lists, filters and positions, with anticipated titles as the initial list where available.
- Upcoming episodes show **Airs today**, **Airs tomorrow** or an expected date; release dates do not guarantee stream availability.
- Settings reveal dependent options only when relevant and omit unsupported Kodi subtitle controls.
- Provider diagnostics distinguish timeouts, connection failures, invalid responses and HTTP errors. Add-on error responses count as failures while other providers continue.

[Browsing and settings guide](docs/discovery.md) · [Player and chapter controls](docs/player-skin.md). Update the companion skin to **0.1.6** and restart Kodi. Player rendering and remote navigation still need checking on your device.

## What's new in 1.8.22

- Search now finds configured catalogues as well as titles. Collections keep their supplied order and offer watched markers, progress and Unwatched only filtering.
- Discover follows Type → Browse group → List, with Highlights, My lists, By genre, Collections, Streaming services and Other lists. Favourites is now My Favourites.
- All lists shows separate rows for the selected group; More lists opens the next batch. Select one named list to focus on it.
- Genre lists merge across suppliers with one genre selection. Extra provider filters remain under Discover options.

[Discover and catalogue search configuration](docs/discovery.md).

## What's new in 1.8.21

- Home contains Continue Watching, Up Next and confirmed Upcoming Episodes from saved series.
- Sports has its own sidebar section.
- Discover merges providers into movie and series categories such as Popular, Trending and All-time Greats, with duplicate titles removed when they share an identity.
- Franchise lists appear under Collections, and network lists under Streaming services. Provider names are available through List sources.

[Discover and Home configuration](docs/discovery.md).

## What's new in 1.8.20

- Preferred provider posters are protected from ordinary catalogue artwork during background updates, independent of row order.
- Background poster requests have the normal 15-second metadata timeout, giving configured artwork more time to resolve without blocking browsing.
- These changes apply to all matching movie/series entries; they do not hard-code individual titles or poster styles.

## What's new in 1.8.19

- Sports-only metadata is excluded from movie/series provider choices, and supplier descriptions explain what metadata support does and does not guarantee.
- Configured AIOMetadata posters are checked in the background and take priority over older catalogue images, preserving integrated poster customisations.
- First and repeat startup measurements have separate rows, with durations displayed in seconds.

## What's new in 1.8.18

This update adds a **Providers** page for details, artwork, supplied ratings, search, streams and subtitles; consistent disabled-catalogue handling; artwork refresh across Library, search and loaded pages; duplicate-aware preferred-provider search; local **Troubleshooting** and startup measurements; faster poster-cache reads; and player menus that close when their video ends or changes.

Automated checks cover these changes. Actual Kodi rendering and remote-focus checks still require a reachable device. [Configuration and validation](docs/provider-and-reliability-pass.md).

## What's new in 1.8.17

- AIOMetadata's configured posters now apply to Continue Watching, Up Next and other catalogue rows, including Trakt, even when titles are absent from AIOMetadata's own catalogue rows.
- Missing posters load in small background batches and share a configuration-aware cache. Artwork updates preserve selection, progress and loaded pages.
- Subtitle download choices show the supplying add-on and reported FPS. Forced-subtitle matching, language filters and subtitles-off defaults are preserved.
- Removed four older font files, replaced remaining display references with bundled Inter weights and added matching font licence notices.

Update both the app and companion skin through **Strem4Kodi Repository**, then **restart Kodi**. The skin dependency updates automatically; select **Strem4Kodi Settings → Appearance → Player appearance → Strem4Kodi Player** if you have not already activated it. Requires **Kodi 21 or later**. [Player configuration and limitations](docs/player-skin.md).
