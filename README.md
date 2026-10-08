<p align="center">
  <img src="https://raw.githubusercontent.com/daanvb/strem4kodi-repository/main/script.strem4kodi/icon.png" width="160" alt="Strem4Kodi blue play logo">
</p>

# Strem4Kodi

**Your Stremio library, built for the Kodi remote.**

Strem4Kodi is daanvb’s independent Kodi addon: a cinematic browsing interface, clearer source selection and configurable playback, using your Stremio account and installed addons. Kodi handles video playback; Strem4Kodi supplies its own browsing interface and an optional companion player skin.

**Latest published version: 1.8.48.** [Install and update](https://daanvb.github.io/strem4kodi-repository/) · [Full changelog](changelog.txt)

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

## What Strem4Kodi includes

| Feature | What it does |
| --- | --- |
| Browsing and details | Title artwork, scrolling descriptions, compact metadata, UK age-rating badges when supplied, cast photos and recommendations. |
| Search | Ranked movie/series suggestions, punctuation-insensitive matching, recent searches and direct title opening, with a native Kodi keyboard option for phone input. |
| Sources | Resolution, reported size, provider, video format, audio, language and other supplied technical information. Filter by source, quality, audio or video format. |
| Auto Play | Separate profiles for movies, series and animated series; closest-match selection and attempts on alternative sources after failure. |
| Trailers | Manual trailers and previews after a configurable focus delay. Continue Watching items do not autoplay trailers. |
| IntroDB | Community intro, recap, outro and post-credits skip buttons when timestamps are available. |
| Up Next | A Home row opens resolved next-episode details; a floating playback card uses credits markers, a series override, learned timing or a fallback. |
| Account sync | Shared library and playback progress through your Stremio account, with queued retries. |
| Smart credits sync | Optional sharing of learned credits timings and series overrides through the private GitHub sync repository. |
| Artwork and ratings | Per-catalogue posters/wide thumbnails, provider visibility and optional TMDB/MDbList enrichment. |
| Subtitles | Kodi subtitle controls, Stremio subtitle downloads and automatic forced subtitles. |

## Install or update

1. Download **Strem4Kodi Repository 1.0.4** from the [repository page](https://daanvb.github.io/strem4kodi-repository/).
2. In Kodi, open **Settings → Add-ons → Install from zip file** and select the repository ZIP. Enable unknown sources if Kodi asks.
3. Open **Install from repository → Strem4Kodi Repository → Program add-ons → Strem4Kodi** and install it.
4. Launch Strem4Kodi and connect your Stremio account using the sign-in screen.

For existing installations, use Kodi’s normal addon update process. If the update is not listed, open the context menu on **Strem4Kodi Repository** under **My add-ons → Add-on repository**, choose **Check for updates**, then check Strem4Kodi again. The repository version (**1.0.4**) and published app version (**1.8.28**) are different numbers.

The repository page also provides a direct app ZIP. Installing it manually is an alternative; you do not need a script for routine updates.

## First-time configuration

Open **Settings** inside Strem4Kodi. Changes save immediately; appearance changes apply when you return to browsing.

### Account & Stremio

Connect the same Stremio account on each device. Your installed Stremio addons provide the catalogues, streams and subtitles they support. Manage them through **Stremio addons**.

**Catalog manifest** selects the main catalogue/metadata provider; it does not replace your installed stream providers. Artwork enhancements such as BetterPosters are applied to matching titles rather than treated as separate browsing categories where wrappers can be identified.

### Startup and the player Back button

**General → Launch when Kodi starts** opens the app after Kodi starts its service. Set **Startup delay → Immediately** to add no intentional wait; the other options add 1, 2, 3 or 5 seconds. Kodi still loads its own skin and services first. Cached Home appears before catalogue refresh work.

Strem4Kodi caches the generated layout and records `startup.layout` and `startup.visible` timings in the local performance profile and Kodi log. These measure the app's own startup, not power-on to Kodi ready.

**Playback → Back during fullscreen playback** offers Kodi default, one press to stop, or two presses to stop. Double Back is the new default unless a previous installation explicitly disabled our Back override. First Back shows a reminder; another Back within three seconds stops playback. This keymap applies to Kodi fullscreen video. Player menus and dialogs retain their normal Back actions. Settings changed inside Strem4Kodi apply immediately; native Kodi add-on settings apply when Strem4Kodi next opens.

**Development update:** Playback → Hide playback controls after adds a five-second inactivity timeout for the control bar during Strem4Kodi playback, with ten/fifteen-second and Kodi-default alternatives. Pause, seeking and audio/subtitle submenus keep the controls visible. This does not change other Kodi playback.

### Search providers and episode descriptions

The typing suggestions use IMDb title autocomplete, with a Cinemeta fallback. Selecting a suggested title opens its details directly. Choose **Search** at the bottom of the keyboard to request the broader provider results; a unique exact suggestion can still open directly instead of showing a results page. Full Search queries Cinemeta and installed movie/series catalogue providers that declare search support, including AIOMetadata when configured. AIOStreams supplies stream sources rather than the title suggestion list.

Series details merge installed metadata providers with the default metadata source. Episode descriptions depend on the returned episode metadata; an overall series synopsis is not an episode synopsis. Strem4Kodi adds a cached TMDB fallback for missing descriptions using your configured TMDB key.

BetterPosters artwork wrappers are supported. Standard catalogues from other Stremio add-ons can be browsed, but companion features that depend on Stremio-specific detail links or playback events are not automatically implemented. More Like This and Content Deep Dive need dedicated contextual integration; they are excluded from generic title autocomplete.

### API keys

All optional credentials are under **Settings → API keys**. API-key fields use Kodi’s native keyboard without search suggestions. Open the field, then use the keyboard/text function in your Kodi phone remote to type or paste.

| Key | Used for |
| --- | --- |
| TMDB | Cast photos, recommendations and exact-season TMDB episode scores. |
| MDBList | Additional movie/overall-series ratings, including Rotten Tomatoes and Metacritic when returned. Supporter API keys can also provide the MDBList episode-rating matrix. |
| GitHub credits sync token | Access to the private `daanvb/strem4kodi-sync` repository for learned credits and series overrides. |

Keys are saved on the device that you configure. Stremio progress sync does not copy these keys to other devices.

### Sources and Auto Play

Under **Sources**, set your preferred quality, video format, audio, language and provider. These preferences rank results; **Maximum stream quality** is the separate ceiling that hides known higher resolutions on this device. Unknown resolution stays available.

For a Full HD screen, choose **Maximum stream quality → 1080p**. For a 4K device, set its own limit and preferences. Source preferences and remembered picker filters are local to each installation.

Under **Auto Play**, configure each content profile:

| Profile | Applies to |
| --- | --- |
| Movies | All movies, including animated movies. |
| Series | Non-animated series episodes. |
| Animated series | Animated series episodes only. |

Choose **Off — choose manually**, **Highlight best match**, or **Auto play best match**. Each preference can inherit from **Sources** or override it for that profile. Autoplay uses the closest eligible match if no exact match exists, respects the maximum quality, and tries different sources up to **Maximum automatic attempts**. If automatic attempts are exhausted, the source picker offers manual selection.

**Play/Resume** appears for autoplay; **Choose source** appears for manual selection. **More → Choose source manually** is available while autoplay is enabled.

### Video formats and FEL

The picker’s **Video** filter includes Dolby Vision, HDR and reported **Profile 7/FEL** options. **Show FEL source hints** controls the extra labels; disabling it does not remove the filters.

These labels distinguish:

- **P7 FEL reported**: the provider or filename explicitly claims Profile 7 with FEL.
- **Profile 7 reported**: Profile 7 is reported, but the enhancement layer may be unknown or MEL.
- **FEL disc available; stream unverified**: the community catalogue lists a FEL disc for this movie; the selected stream/edition has not been verified.

A Dolby Vision or REMUX label alone does not prove FEL. The addon currently does not inspect the actual video bitstream before playback. A companion file analyser is a future project, not part of this release.

CoreELEC on a suitable Ugoos setup, Shield, Fire TV and smart-TV Kodi installations use Kodi’s native playback capabilities. Supported formats depend on the device, operating system, Kodi build, stream and audio/video equipment. Full interface quality is the default; **Reduce interface load** is optional and does not change video decoding.

### Ratings

Each **Show Movie Rating - [provider]** switch controls movies and the overall series score, and enables that provider for episodes. The immediately following **Show Episode Rating - [provider]** switch controls episode cards only. **Both switches must be on to show that provider on episodes.**

Missing episode scores stay blank. Strem4Kodi never substitutes a show’s overall score for an episode score. TMDB episode scores need your TMDB key; Rotten Tomatoes, Trakt and Metacritic episode scores appear only when the episode metadata actually supplies them. Enabling a switch cannot create a score that the provider does not return.

For MDBList episode scores, enter your key under **API keys**, then enable **Show Movie Rating - MDBList score** and **Show Episode Rating - MDBList** under **Ratings**. The [documented episode matrix](https://api.mdblist.com/docs/) requires an MDBList Supporter account. Free accounts return an aggregate summary, which is not displayed on episode cards. A single cached response supplies all seasons; scores are matched by season and episode number and labelled MDBList, not IMDb or Rotten Tomatoes.

Scores out of ten show one decimal place. Percentage ratings remain percentages. **Appearance → Ratings** controls hero/details badges; use the episode switches for episode cards.

### Trailers

Enable **Allow trailers** and **Play trailers automatically**, choose where previews may play, then set **Wait before playing a trailer**. Keep the same title highlighted for that delay; moving focus resets the wait. Previews use available direct IMDb trailers and your selected trailer quality. Continue Watching items are excluded from automatic previews.

A title without a resolvable trailer will not preview. The configured delay does not guarantee immediate playback if the trailer request is still loading.

### IntroDB and Up Next

Under **Skip & Up Next**, enable IntroDB and the skip-button types you want. No IntroDB API key is required. Buttons appear only during a matching community marker; coverage varies by episode.

Up Next offers the next regular aired episode, including across season boundaries. Its timing uses the episode’s credits marker first, followed by a series override, reliable learned timing, or **Up Next fallback timing**. **Learn credits timing per series** needs at least three played episodes with usable IntroDB markers; it does not guess credits by analysing video. Set a series-specific override through the episode menu when needed.

To share learned credits and overrides:

1. Create a fine-grained GitHub token restricted to the private **`daanvb/strem4kodi-sync`** repository, with **Contents: read/write** access.
2. Enter it under **API keys → GitHub credits sync token** on each device.
3. Enable **Account & Stremio → Sync smart credits between devices** and check **Smart credits sync** for the result.

The sync repository is currently fixed in the code. A token for another repository will not work. GitHub sync carries credits timings and overrides, not watch progress or API keys.

### Appearance and spoiler protection

Choose your theme, focus colour, title logos and visible metadata under **Appearance**. **Catalogue thumbnails** sets Posters or Wide thumbnails separately for each installed catalogue.

**Episode spoiler protection** offers:

- **Off**: use supplied artwork, including any blur already added by the provider.
- **Blur unwatched episodes**: soften artwork for unwatched episodes locally using Kodi’s texture handling.
- **Blur unless provider artwork**: keep provider episode thumbnails untouched; soften fallback artwork when no episode thumbnail is supplied.

Watched episodes use the original supplied image. Off cannot reconstruct an image the provider already blurred.

## Sync and troubleshooting

| What you see | What to check |
| --- | --- |
| Updates pending on Account sync | These are queued watch-progress changes, not app updates. Use Sync account now and read Progress upload status. |
| Progress differs between devices | Use the same Stremio account; allow time for upload and idle refresh. Progress uploads during playback about every 30 seconds, with pause/stop checkpoints; idle devices refresh about every minute. |
| No sources match | Clear picker filters, check Maximum stream quality, and confirm the account’s stream addons. A FEL filter requires an explicit layer report. |
| Size/audio/video unreported | The provider may not supply that information. The addon parses available fields and release text; it does not download the full file to fill gaps. |
| A source fails | Autoplay can try alternatives. Manual selection remains available; a source that plays an error video may need manual rejection because Kodi can treat it as successful playback. |
| No Rotten Tomatoes episode badge | Check both rating switches and whether the metadata contains an actual episode score. MDbList’s show-level score is not an episode score. |
| No trailer | Check Allow trailers, automatic preview scope and delay; some titles have no available trailer. |
| Smart credits not shared | Check the GitHub token, its access to the fixed private repository and the Smart credits sync status. |
| New update not listed | Refresh the repository and confirm repository 1.0.4. Check the app version separately. |

Watch-progress sync uses Stremio’s library state, watched flags and episode state. It is not an exhaustive timestamped viewing-event history. Concurrent playback of the same title follows newer remote activity; queued older progress is protected against overwriting newer server state.

## Data and privacy

- Account credentials, API keys, caches, recent searches and queued progress are stored in Kodi’s Strem4Kodi addon profile on each device.
- Account/library progress is shared with Stremio. Metadata, streams and subtitles are requested from the services/addons you configure.
- IntroDB receives episode lookups.
- Smart credits sync is opt-in and uses the private GitHub repository. The public FEL hints catalogue downloads without sending your viewing history.
- Diagnostics remain local; no remote reporting endpoint is enabled in this project.

## Source, builds and credits

Development source: **`daanvb/Stremio-for-Kodi-private`**, branch **`strem4kodi`**. Public Kodi feed: **`daanvb/strem4kodi-repository`**, branch **`main`**. The source repository requires access; installable ZIPs contain the addon source.

```sh
python -m unittest discover -s tests
python tools/build-stremio-addon.py --output dist
```

Strem4Kodi develops independently from the original project. Useful upstream fixes can be reviewed on demand with `python tools/review-upstream.py --output dist/upstream-review.md`, then adapted individually. Nothing is merged automatically. See the [upstream review guide](https://github.com/daanvb/Stremio-for-Kodi-private/blob/strem4kodi/docs/upstream-review.md).

The addon ID is **`script.strem4kodi`**; repository ID is **`repository.strem4kodi`**. The repository builder requires an explicit HTTPS `--feed-url`. Use a new version for a new published build rather than replacing an existing release ZIP.

Based on [Stremio-for-Kodi](https://github.com/0eroiQ/Stremio-for-Kodi), with Nimbus layouts/artwork credited to Ivar Brandt. Original contributor credits, Git history, bundled third-party notices and the **GPL-2.0-or-later** license are retained. [IntroDB](https://introdb.app/), TMDB, IMDb and MDbList supply the respective external metadata; the [community FEL disc catalogue](https://github.com/Appz4Fun/fel-dolby-vision-movies) supplies disc hints.

Strem4Kodi uses the TMDB API but is not endorsed or certified by TMDB. It is an unofficial community project, not endorsed by Kodi or Stremio. Strem4Kodi’s cyan wordmark and blue play branding belong to this project.
