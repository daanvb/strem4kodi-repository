# Earlier release highlights

Historical behaviour below describes those releases; use the configuration guide for current setup.

## What's new in 1.8.212

- Complete skin settings labels and codec-logo options.
- Add P3i playback/Dolby Vision details and runtime MEL/FEL indicators with companion skin **0.1.37**.

## What's new in 1.8.149

- Reuse parsed source display data within each list update and publish cards through Kodi's bulk-list API.
- Preserve ranking, filters, duplicate/service grouping, selection, autoplay and cancellation. Rebuild derived data for later arrivals and metadata changes.
- Synthetic PC tests measured 62–64% less local result-delivery time; actual device gains need normal-use comparison. Provider response times remain outside this improvement. Player skin remains **0.1.26**; installer remains **1.0.4**.

## What's new in 1.8.148

- Fix the first source-search upload: the report file does not exist yet, and that expected response was incorrectly treated as a token-access failure.
- After updating, use **Settings > Troubleshooting > Send source-search report** again. Existing measurements are preserved; genuine access errors and upload read-back checks remain enforced.
- Player skin remains **0.1.26**; installer remains **1.0.4**. Actual device upload remains for normal-use validation.

## What's new in 1.8.147

- **Settings > Troubleshooting > Last source search** shows saved provider timings without starting playback. Existing 1.8.146 measurements can be viewed after updating.
- **Send source-search report** opens a Send/Cancel review, then uses the configured private reporting service for a timing-only upload. Check **Source-search upload** for verified success or failure.
- No Kodi logs, titles, stream URLs or account details are collected by this upload. Private diagnostic reporting and its token must already be configured. Player skin remains **0.1.26**; installer remains **1.0.4**.

## What's new in 1.8.146

- Measure provider response, local source parsing and result delivery in the background during normal searches.
- Keep bounded timings and fixed provider-family labels for the existing explicit performance report; no extra provider requests, polling or automatic uploads.
- These measurements help locate search delays; they cannot inspect upstream internal work or Kodi frame rendering. Player skin remains **0.1.26**; installer remains **1.0.4**.

## What's new in 1.8.145

- Recognise AIOStreams' icon-prefixed Ready (TB/RD) reports for the source-card badge and named service in details.
- Ignore display icons and formatting while preserving explicit service evidence and conflicting-report checks.
- Refresh older cached unknown results after updating. Player skin remains **0.1.26**; installer remains **1.0.4**. Native appearance needs normal-use testing.

## What's new in 1.8.144

- Recognise reported `Ready (TB) Comet` / `Ready (RD) Comet` labels for the source-card service badge.
- Show **Service: TorBox (TB)** or **Service: Real-Debrid (RD)** in source details.
- Refresh older cached unknown results after updating. Player skin remains **0.1.26**; installer remains **1.0.4**.

## What's new in 1.8.143

- Recover transient movie/episode source-search failures with one bounded retry; keep healthy partial results available.
- Refresh incomplete cached results before best-quality autoplay and Up Next; preserve Fastest start and live-search behavior.
- Show **RD** / **TB** in the source-card corner when Real-Debrid / TorBox is explicitly reported; keep service alternatives separate.
- Player skin remains **0.1.26** and installer remains **1.0.4**. Actual provider responses and native appearance need normal-use testing.

## What's new in 1.8.142

- Search up to eight source providers concurrently and reduce repeated result processing.
- Select the top visible result when a source search or Refresh finishes; preserve navigation while results arrive.
- Keep the EPG highlight and selected-event text aligned when Kodi focus updates lag; ignore stale row activations during the transition.
- Player skin remains **0.1.26**. Actual search speed depends on provider responses; native behavior is verified through normal use and bug reports.

## What's new in 1.8.141

- Keep Sports loading responsive and cancellable; preserve guide selection, timeline and competition filters when returning.
- Improve fixture matching, shared schedule caching and recovery when a provider fails.
- Hide postponed/cancelled fixtures from Live Now while keeping them labelled and selectable elsewhere.
- Refresh the visible guide once per minute without extra provider requests; pause refresh during dialogs and playback.
- Player skin remains **0.1.26**. Automated checks pass; normal device testing and bug reports will follow publication.

## What's new in 1.8.140

- Align IMDb episode titles, numbering and playback requests while preserving preferred artwork and watched history.
- Keep resume and offline progress visible, preserve another episode's active position, and verify watched-state updates.
- Improve window/service cleanup, custom unpause recap, source/episode handoffs and player-control ownership.
- Reduce cache/Home overhead and keep Discover responsive while lists and rankings load.
- Includes player skin **0.1.26**. Held-Back versus intentional double-Back remains unresolved; physical-device validation is still required.

## What's new in 1.8.139

- Place Streaming services directly below Highlights in Discover.
- Promote already-loaded Popular/Trending titles within streaming-service genre results, including All lists and loaded pages; preserve provider order when ranking is unavailable.
- Fit Sports loading artwork in a larger landscape frame so both team logos remain visible; preserve portrait movie/series layouts.

## What's new in 1.8.138

- Filter Discover All lists by genre across supporting catalogues, preserving original provider options and restarting pagination.
- Distinguish sports leagues by stable API identity and country so equal league names cannot mix competitions.
- Allow Aerial after the configured idle interval while video is paused; active playback remains protected.

## What's new in 1.8.137

- Filter selected streaming-service catalogues directly in Discover using the choices supplied by installed add-ons.
- Remove personal favourites, watchlists, watch history and recommendations from Discover; retain Community Favourites and Sports.
- Available filters vary by catalogue. An older-kid/young-teen age filter is not included.

## What's new in 1.8.136

- Preserve best technical quality on resume; provider health breaks technical ties without promoting lower-quality releases.
- Recover automatic VOD playback after 12 continuous seconds of confirmed, unpaused buffering, retaining episode and position.
- Put Report wrong episode first in Settings and refresh viewer conflict choices when progress changes during review.

## What's new in 1.8.135

- Keep background playback recovery running after transient player/window or details-refresh errors during source handoff.
- Continue the existing polling cadence and preserve recovery and cancellation behavior.

## What's new in 1.8.134

- Keep automatic startup recovery armed when Kodi clears the native item during AV or ambiguous Stop/End callbacks.
- Let the existing startup timeout retry another source for the same episode and resume point.
- Trace this callback path without recording native exception messages.

## What's new in 1.8.133

- Retry owned automatic episode sources that stop before AV starts through the existing bounded alternate-source flow.
- Preserve the selected episode and deliberate double-Back cancellation, including when Kodi clears the playing file.

## What's new in 1.8.132

- Stop showing untimed live events or confirmed finished matches as live after an explicit unavailable-source response.
- Restore availability when playable sources return, while preserving in-progress and continuous-feed safeguards.
- Expand sports-guide descriptions by removing the redundant bottom remote hint strip.

## What's new in 1.8.131

- Keep LIVE labels for untimed events without painting an implied full-width interval; 24hr Feeds retain their continuous lane.
- Match reversed club order and common football names while requiring one unique fixture.
- Refresh fixtures before displaying the guide, with a five-minute cache for quick reopenings.

## What's new in 1.8.130

- Filter football guide rows by competition using matched Live Football API league names.
- Choose All competitions to keep every listing; filtering is local and uses no extra API request.
- Keep selector focus across minute refreshes and reset the filter when changing sports lists.

## What's new in 1.8.129

- Optionally enrich football guide rows with matched kick-off times using your own Live Football API key in Sports guide settings.
- Keep provider times authoritative, show pre-match coverage separately from kick-off, and extend estimated coverage during extra time.
- Cache the daily fixture list for one hour; retain possible post-match coverage after a fixture finishes.

## What's new in 1.8.128

- Keep a branded transition cover visible while leaving the Sports guide for another destination.
- Show the active viewer as a separate clickable sidebar header and refresh the navigation icons.
- Simplify upcoming episode broadcast labels while retaining matched UK airing times.

## What's new in 1.8.127

- Move the active profile to the top of the sidebar and keep the sports guide visible behind its sidebar menu.
- Show matched TV broadcast times for upcoming episodes, with a network label and TVmaze attribution.
- Keep explicit Mark as Watched and Mark as Unwatched actions in Continue Watching.

## What's new in 1.8.126

- Improve viewer switching with a separated profile row, clearer avatar and covered transition.
- Return from the sports guide to the sidebar; show upcoming episode air schedules and prevent early source searches.
- Simplify media context menus and clarify Share Watch Progress.

## What's new in 1.8.125

- Switch viewers from the sidebar, copy Master into an independent profile, and share one title’s progress once from Continue Watching.
- Improve sports expiry and source timing; keep continuous 24hr Feeds first.

## What's new in 1.8.124

- Deliver the viewer profile activation fix through a new Kodi update version. Fire TV setup still needs a device retest.

## What's new in 1.8.123

- Handle malformed provider catalogue and library metadata without crashing Discover or library sections.
- Complete playback cancellation if Kodi cannot start a close or cleanup worker thread.
- Keep competing same-viewer progress for review in Viewer profiles when devices sync; different viewers continue to hold separate play times. Skin remains 0.1.25. Physical Kodi/CoreELEC validation is still needed.
- Make first-time Viewer profile setup reliable on active devices, even while Kodi is rotating local stores. Preserve recovery copies, verify that activation is saved, and report a retryable error instead of returning to the setup prompt.

## What's new in 1.8.122

- Keep already-UK kick-off labels at the supplied time and retain row focus when scrolling the sports guide. Order sports lists Live Now, Football, then alphabetically.
- Highlight live games in green with duration/end markers and attach a NOW clock to the ruler. Missing ends use the existing 150-minute estimate, marked **~**; undated live streams do not gain invented timings.
- Default sports sources to highest reported bitrate without changing movie/series sorting. Safely initialise sorting before details metadata loads. Skin remains 0.1.25; native remote/rendering validation remains necessary.

## What's new in 1.8.121

- Centre EPG button text horizontally and vertically, including the sport selector while keeping its dropdown arrow clear.
- Fix player shortcuts rejecting Kodi's no-modal-dialog state, which could prevent Down from opening controls. Keep related player handlers consistent, protect actual modal menus, and preserve double-Back stopping and sports recovery. Skin remains 0.1.25.
- This fixes a reproduced shortcut defect; the full reported CoreELEC/TV-remote lockup still needs device validation.

## What's new in 1.8.120

- Change the sports list without leaving the EPG. The selector opens over the guide and refreshes the chosen list in place, keeping the timeline position.
- Use smaller, evenly spaced header buttons, with Close beside the other actions. Cancelled selections and failed loads preserve the current guide. Skin remains 0.1.25.

## What's new in 1.8.119

- **Sports opens straight into the EPG**, with the sport selector at the top and direct source selection when you choose an event. Returning from sources restores your guide position.
- See gold kick-off markers and UK times with GMT/BST handled automatically. Where no end is supplied, events are assumed live for 2.5 hours after kick-off.
- Cleaner pill buttons, fewer notices and a larger scrolling description panel. Move the timeline with Left/Right on the remote; no external guide feed is needed. Skin remains 0.1.25.

## What's new in 1.8.118

- Open **Sports → TV guide** for channel/event rows, live status, provider descriptions and a local-time ruler. Browse with the remote and press OK to open the existing sports source picker.
- Use the sports catalogue already configured in Stremio. Missing programme times are labelled explicitly; no external guide feed is needed. More listings retains provider pagination.
- Player skin remains 0.1.25. Native Kodi/CoreELEC rendering, remote input and playback from the guide still require device verification.

## What's new in 1.8.117

- Add optional viewer profiles, each with separate Continue Watching, watch history, favourites, Watch Later and saved lists, while sharing Stremio login, providers and device settings.
- Support private viewer-list sync between devices and preserve the previous shared behaviour until viewer profiles are enabled. Devices may be updated individually; older clients do not understand viewer-specific changes.
- Player skin remains 0.1.25. Updating and restarting Kodi is recommended; profile switching and cross-device playback still need physical-device verification. See the [full changelog](../changelog.txt) for releases 1.8.113–1.8.116.

## What's new in 1.8.112

- Keep direct Up Next playback covered and scroll long episode titles.
- Prefer English dialogue audio and current autoplay format settings over older weaker sources.
- Correct pause/resume rewind handling, expire skip buttons promptly, align the last Home row page and simplify Continue Watching actions.
- Update the app and restart Kodi. Skin remains 0.1.25. Native device playback still requires confirmation. [Release and validation](release-1.8.112.md).

## What's new in 1.8.111

- Add optional saved-progress resume rewind beside Unpause rewind, from 3 seconds to 1 minute. Off by default; included in device setup copies.
- Sort time choices while preserving existing settings and profile values.
- Improve right-edge focus scrolling, Recent Searches artwork and watched/unwatched eye icons.
- All 1,899 Windows tests passed. Update the app and restart Kodi; skin remains 0.1.25. Physical TV verification remains necessary. [Release and validation](release-1.8.111.md).

## What's new in 1.8.110

- Allow delayed first CEC OK repeats and retain safe release-only context dispatch. Raw CEC short taps may wait up to 750 ms; physical Ugoos holds still need verification.
- Remove the Up Next artwork fade and idle prompt, retaining useful source-search status.
- Use a clearer Watch from Beginning icon with a fresh texture filename.
- Restore recent-search dialogs on Back even during the input cooldown after opening a collection.
- All 1,883 Windows automated tests passed. Update the app and restart Kodi; skin remains 0.1.25. [Release and validation](release-1.8.110.md).

## What's new in 1.8.109

- Read missing chapter names from supported playing files without downloading the video or seeking playback. No extra client software is required; unsupported sources keep native/numbered chapters.
- Improve pre-roll fullscreen coverage, HDMI-CEC held OK and native pause-rewind handover.
- Restore collection progress, promote the next episode name in Up Next, and replace the Watch from Beginning icon.
- All 1,878 automated tests passed. Update the app and restart Kodi. Skin remains 0.1.25. Physical remote/audio behaviour still needs verification. [Release and validation](release-1.8.109.md).

## What's new in 1.8.108

- Improve title and episode responsiveness on slower devices, prevent stacked title screens, and protect saved Resume positions.
- Strengthen Play Next handovers and redirected episode metadata; keep late callbacks from cancelling a new request.
- Automatically keep the last ten playback diagnostic reports per device, including redacted Kodi logs, with verified private upload while idle.
- Update the app and restart Kodi. Skin remains 0.1.25. Native Toshiba playback still needs device verification. [Release and validation](release-1.8.108.md).

## What's new in 1.8.107

- Preserve larger redacted Kodi technical logs across restarts and upload verified compressed attachments to your private diagnostic repository.
- Add Play Next/source/progress checkpoints, safe worker/service failure locations and explicit Android crash-buffer access status.
- Measure first/repeat startup through initial Home, catalogue refresh and artwork completion. No per-frame tracing or automatic uploads during playback.
- Update the app and restart Kodi. Skin remains 0.1.25. The Fire TV Play Next crash still requires fresh device evidence. [Release details](release-1.8.107.md).

## What's new in 1.8.106

- Prepare recap rewind while paused, preserving immediate native Play without a later jump.
- Improve pre-roll loading coverage, Atmos matching, stalled-intro recovery and ordinary HDMI-CEC OK playback controls.
- Make portrait cards about 9% larger, fix first-poster clipping and sharpen menu/action icons and poster borders.
- Add safe CEC hold and audio diagnostics. All 1,781 automated tests passed; physical Shield audio and TV-remote behaviour still require verification. Skin remains 0.1.25; restart Kodi after updating. [Release and validation](release-1.8.106.md).

## What's new in 1.8.105

- Keep returns to Search/collections covered until the restored results are ready.
- Start the branded splash earlier and remove unnecessary imports from ordinary launches.
- Let title details become usable before optional ratings, quality fallback and recommendations finish. Preserve episode readiness, focus and source-first quality. Skin remains 0.1.25; restart Kodi after updating. [Release and validation](release-1.8.105.md).

## What's new in 1.8.104

- Fix stuck title loading from Search and collections, retaining the selected results and Back route.
- Add a branded startup splash and bounded recovery when Kodi refuses a window activation.
- Keep native-window retirement and cleanup safeguards. Skin remains 0.1.25; restart Kodi after updating. [Release and audit](release-1.8.104.md).

## What's new in 1.8.103

- Keep the transition from Search/collections covered while stopping trailers and opening movie details.
- Silence repeated hold-Left clicks and restore navigation sounds automatically.
- Show the installed app version in Settings. Skin remains 0.1.25; restart Kodi after updating. [Release details](release-1.8.103.md).

## What's new in 1.8.102

- Improve movie handoffs from Search/collections and loading-card coverage for manual and automatic playback.
- Correct low poster progress fills; use hold Left at the row edge to open the menu on every device.
- Protect slow/startup actions from queued OK presses and keep background updates from changing the selected poster.
- Reject stale worker results, remove duplicate posters and reduce artwork thread creation. Skin remains 0.1.25; restart Kodi after updating. [Release and validation](release-1.8.102.md).

## What's new in 1.8.101

- Move inactive movies and series from Continue Watching to Don't Forget About Me after 30 days; remove their Home cards after another 30 days while keeping progress.
- Watching again resets the clock. Explicit IDs prevent duplicate cards, and moved titles retain their resume/next-episode target and removal action.
- Speed up unchanged Home refreshes and keep cached row order, timezone handling and malformed-state recovery consistent.
- All 1,678 automated tests passed. Skin remains 0.1.25; restart Kodi after updating. [Retention guide](continue-watching-retention.md) · [Audit details](home-retention-audit-2026-10-14.md).

## What's new in 1.8.100

- Include Auto Play profiles and portable playback, subtitle and skip preferences in Shield setup copies.
- Player skin 0.1.25 installs Aerial from Kodi's official repository. Approved profile setup selects it, with backup and Undo; its settings open from Skin Settings / General.
- Give the private setup dashboard Strem4Kodi branding, clearer phone approvals and a manual TV-code entry.
- All 1,661 automated tests passed. Update the Shield and receiving devices, capture a fresh master, then import it on each device including the Shield and restart Kodi. Native Aerial activation still needs a device check. [Setup details](device-setup.md).

## What's new in 1.8.99

- Private profile imports now configure Kodi Home to show Add-ons and Favourites, with category widgets enabled.
- Apply the requested logging, HTTP and local application-control settings and unknown sources, with backup, readback, retry and Undo.
- Fix setup dashboard sign-in behind Caddy without weakening Origin/CSRF checks.
- Player skin 0.1.24. All 1,644 automated tests passed. Restart Kodi, then import your private setup profile to apply these defaults. Native Kodi confirmation prompts remain. [Setup details](device-setup.md).

## What's new in 1.8.98

- Show the next episode title and prepare its sources before the current episode finishes; retain natural-end autoplay and source recovery.
- Preserve progress when Kodi's stop callback exposes a reset clock. Play/Resume now follows the highlighted episode, including unfinished rewatches.
- Keep background progress/recovery running after an optional watcher error; guard slow native-window transitions and clean shutdown.
- Reduce work during search typing and bound hero-cache memory during long browsing sessions.
- Player skin remains 0.1.23. Restart Kodi after updating. All 1,632 automated tests passed; Fire TV card rendering and handoff speed still need a device retest. [Audit details](app-audit-2026-10-14.md).

## What's new in 1.8.97

- Copy preferred S4K settings from your master device through private setup, with a QR code and owner approval on your phone.
- Apply API keys and provider selections with backup, retry and Undo. Stremio account sign-in stays on its official page.
- Existing signed-in devices keep their normal startup; audio/display hardware and custom remote keymaps remain device-specific.
- Start on the Shield: Settings → Account & Stremio → Copy setup profile from this device. Then approve new devices through the setup dashboard. [Setup guide](device-setup.md).
- Player skin remains 0.1.23. Restart Kodi after updating. Automated checks and private HTTPS passed; native device enrollment still needs testing.

## What's new in 1.8.96

- Keep titles in the search suggestions while their artwork refreshes, fixing omissions such as The Jinx and This Country.
- Reduce work during rapid browsing: enrich the latest settled title, show cached details immediately and skip redundant hero redraws.
- Show ready posters without waiting for the slowest lookup in each batch, while retaining row order and cancellation safeguards.
- Player skin remains 0.1.23. Restart Kodi after updating. Automated checks passed; scrolling smoothness needs testing on your device.

## What's new in 1.8.95

- Avoid Kodi Omega's unsafe XML edit-control wrapper in Search. Remote typing remains available; selecting the query field opens Kodi's keyboard for keyboard/phone input.
- Wait for the search worker and native dialog to close before opening a selected title, and safely stop an incomplete handoff.
- Add private search-retirement checkpoints and Python process bitness to help investigate native crashes without exporting search text or credentials.
- Player skin remains 0.1.23. Restart Kodi after updating. The user subsequently confirmed that search selection works on their tested Fire TV; other devices remain unverified.

## What's new in 1.8.94

- Prefer source-derived and shared database quality logos in the hero; PostersPlus fills missing format families and continues to supply poster artwork.
- Try AIOmetadata first and keep other artwork neutral until checked, including Favourites and Watch Later. Clear responses and matching Kodi artwork together while retaining progress and saved lists.
- Preserve poster/episode focus when trailers return from fullscreen; keep poster focus borders clear of the top artwork chip.
- Use native episode progress bars and valid per-episode/measured runtimes; guard repeated OK presses across loading transitions.
- Tighten You May Also Like with recommendations and matching weekly trends, excluding saved, continuing and completed titles. Use configured PostersPlus artwork on similar-title cards.
- Clear completed media loading messages and remove background format-check text. Player skin remains 0.1.23. Restart Kodi after updating; device rendering and crash confirmation still need a device retest.

## What's new in 1.8.93

- Use configured provider artwork for posters, landscape cards and title logos; remove native poster-tag overlays and their setting.
- Invalidate legacy artwork caches and generated tag layouts so old badges do not return from saved rows or fallback images.
- Read PostersPlus quality facts for hero badges, retaining cached source formats and authoritative selected-source/Kodi details.
- Remove the retired background format scanner and tag-only diagnostics.
- Player skin remains 0.1.23. Restart Kodi after updating. The remaining Search crash still requires device diagnosis; this release does not claim to resolve it.

## What's new in 1.8.92

- Add readable technical excerpts from current and previous Kodi logs to existing private diagnostic reports.
- Retain GUI control/window errors, timestamps and addon traceback locations while omitting sensitive or unrecognised message text.
- The remaining Search crash is still under investigation; this update collects the evidence needed to diagnose it.
- Player skin remains 0.1.23. Restart Kodi after updating. After reproducing a crash, reopen Kodi and use Troubleshooting → Send diagnostic report now.

## What's new in 1.8.91

- Guard both Search title-opening paths, close retired controls safely, and restore the originating search screen.
- Correct the parent series/episode metadata handoff used by Up Next.
- Restore chart membership and AIOMetadata poster tags, use rounded boxes, and let current rank/status/director facts appear ahead of lifetime awards.
- Add focused crash/session, installed-code and poster-tag diagnostics, with a Send diagnostic report now action in Troubleshooting.
- Player skin remains 0.1.23. Restart Kodi after updating. Fire TV crash confirmation requires a device retest.

## What's new in 1.8.90

- Avoid overlapping full Kodi windows when opening a title from Search, then restore the exact results and selection on return.
- Invalidate stale cached award labels and reject ambiguous combined-award list claims.
- Centre contextual tags at the absolute top of normal and compact posters.
- Player skin remains 0.1.23. Restart Kodi after updating.

## What's new in 1.8.89

- Harden Search title opening and reduce background work while browsing, while retaining focused logo/source checks.
- Correct repeated Up Next titles and add optional, bounded next-episode autoplay after a confirmed natural ending.
- Add session-scoped Play random episode across aired regular episodes from every season, continuing through Up Next and autoplay.
- Keep automatic source discovery alive through Kodi's normal no-video handoff gap after an episode ends.
- Player skin remains 0.1.23. Restart Kodi after updating.

## What's new in 1.8.88

- Keep technical quality indicators in the hero, including focused and trailer preloading; remove poster quality badges and their Appearance setting.
- Place contextual and Trending poster sashes at the very top in natural title case.
- Put Exit app in a smaller separated main-menu footer with a clear power icon; preserve its focus during background refresh.
- Player skin remains 0.1.23. Restart Kodi after updating.

## What's new in 1.8.87

- Keep poster artwork durable in the cache and make native trend and format tags clearer.
- Improve player menu restoration, wrong-episode reporting, and sidebar Exit behavior.
- Make the Windows test runner and profile migration more reliable.
- Player skin remains 0.1.23. Restart Kodi after updating.

## What's new in 1.8.86

- Show upcoming episodes for series in Continue Watching, Favourites or Watch Later, then retain a short post-finale reminder in Don't Forget About Me.
- Add native Trending/New and 4K/Dolby Vision/Atmos poster badges, each group controlled by a switch under Appearance.
- Keep a cancelled trailer from starting late, improve displayed episode runtimes, and put Exit app at the bottom of Settings. Held OK opens context menus on compatible keyboard/HID remotes; ordinary OK is preserved on IR remotes.
- Player skin remains 0.1.23. Restart Kodi after updating; live device behavior still needs confirmation.

## What's new in 1.8.85

- Improve You May Also Like ranking with genre fit, support multiple recommendation seeds, and invalidate older cached results.
- Refine Back navigation, Settings focus and Exit app access; widen Dolby logo badges and move them inward from the right edge.
- Player skin remains 0.1.23. Restart Kodi after updating.

## What's new in 1.8.84

- Sync Continue Watching removals and You May Also Like cards through the existing private GitHub saved-lists sync on devices using the same Stremio account.
- Keep pending progress until Stremio confirms it, and reconcile older refreshes with newer playback across devices.
- Player skin remains 0.1.23. Restart Kodi after updating; cross-device behaviour still needs device confirmation.

## What's new in 1.8.83

- Keep recently watched series in Continue Watching for 30 days, opening the next available episode and respecting manual removal.
- Show up to ten You May Also Like suggestions after completed viewing. Sequel films come first when available; otherwise suggest similar films or shows.
- Load suggestions in the background and keep saved cards through temporary metadata outages.
- Player skin remains 0.1.23. Restart Kodi after updating; native remote behaviour needs device confirmation.

## What's new in 1.8.82

- Show a broadcaster or channel beside a live source when that source reports it. Keep catalogue-wide source names clearly labelled as event-level information; number feeds whose individual identities are unreported.
- Stop or Back from sports playback returns to that event's source picker with the selected source retained.
- Refresh live cache, bitrate and queue statistics in a fixed Media info line without resetting the scrolling Kodi details.
- Player skin remains 0.1.23. Restart Kodi after updating; native remote behaviour needs device confirmation.

## What's new in 1.8.81

- Reconnect app-owned live sports playback after sustained buffering or a playback error, with bounded retries and a cancellable loading card. A new source selection cancels the old reconnect.
- Show available live playback statistics in the player's More Info panel, and add an opt-in private GitHub diagnostic report from that panel.
- Player skin remains 0.1.23. Restart Kodi after updating; native live playback and report upload still need device confirmation.

## What's new in 1.8.80

- Report an incorrect episode directly from the currently playing source in Troubleshooting, with a confirmation and Undo. Autoplay avoids that exact source for the episode on this device.
- Make loading Cancel respond immediately and prevent late retries. Improve Up Next recovery and keep error videos from counting as watched playback.
- Rank automatic sources using confirmed playback history and temporary provider health; a source counts as successful only after playback advances.
- Player skin remains 0.1.23. Restart Kodi after updating; native playback still needs device confirmation.

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

[Browsing and settings guide](discovery.md) · [Player and chapter controls](player-skin.md). Update the companion skin to **0.1.6** and restart Kodi. Player rendering and remote navigation still need checking on your device.

## What's new in 1.8.22

- Search now finds configured catalogues as well as titles. Collections keep their supplied order and offer watched markers, progress and Unwatched only filtering.
- Discover follows Type → Browse group → List, with Highlights, My lists, By genre, Collections, Streaming services and Other lists. Favourites is now My Favourites.
- All lists shows separate rows for the selected group; More lists opens the next batch. Select one named list to focus on it.
- Genre lists merge across suppliers with one genre selection. Extra provider filters remain under Discover options.

[Discover and catalogue search configuration](discovery.md).

## What's new in 1.8.21

- Home contains Continue Watching, Up Next and confirmed Upcoming Episodes from saved series.
- Sports has its own sidebar section.
- Discover merges providers into movie and series categories such as Popular, Trending and All-time Greats, with duplicate titles removed when they share an identity.
- Franchise lists appear under Collections, and network lists under Streaming services. Provider names are available through List sources.

[Discover and Home configuration](discovery.md).

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

Automated checks cover these changes. Actual Kodi rendering and remote-focus checks still require a reachable device. [Configuration and validation](provider-and-reliability-pass.md).

## What's new in 1.8.17

- AIOMetadata's configured posters now apply to Continue Watching, Up Next and other catalogue rows, including Trakt, even when titles are absent from AIOMetadata's own catalogue rows.
- Missing posters load in small background batches and share a configuration-aware cache. Artwork updates preserve selection, progress and loaded pages.
- Subtitle download choices show the supplying add-on and reported FPS. Forced-subtitle matching, language filters and subtitles-off defaults are preserved.
- Removed four older font files, replaced remaining display references with bundled Inter weights and added matching font licence notices.

Update both the app and companion skin through **Strem4Kodi Repository**, then **restart Kodi**. The skin dependency updates automatically; select **Strem4Kodi Settings → Appearance → Player appearance → Strem4Kodi Player** if you have not already activated it. Requires **Kodi 21 or later**. [Player configuration and limitations](player-skin.md).
