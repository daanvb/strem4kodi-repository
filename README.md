<p align="center">
  <img src="https://raw.githubusercontent.com/daanvb/strem4kodi-repository/main/script.strem4kodi/icon.png" width="160" alt="Strem4Kodi blue play logo">
</p>

# Strem4Kodi

**Your Stremio library, built for the Kodi remote.**

Strem4Kodi is daanvb’s independent Kodi addon: a cinematic browsing interface, clearer source selection and configurable playback, using your Stremio account and installed addons. Kodi handles video playback; Strem4Kodi supplies its own browsing interface and an optional companion player skin.

**Latest release: 1.8.138.** [Install and update](https://daanvb.github.io/strem4kodi-repository/) · [Full changelog](changelog.txt)

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
- Player skin remains 0.1.25. Updating and restarting Kodi is recommended; profile switching and cross-device playback still need physical-device verification. See the [full changelog](changelog.txt) for releases 1.8.113–1.8.116.

## What's new in 1.8.112

- Keep direct Up Next playback covered and scroll long episode titles.
- Prefer English dialogue audio and current autoplay format settings over older weaker sources.
- Correct pause/resume rewind handling, expire skip buttons promptly, align the last Home row page and simplify Continue Watching actions.
- Update the app and restart Kodi. Skin remains 0.1.25. Native device playback still requires confirmation. [Release and validation](docs/release-1.8.112.md).

## What's new in 1.8.111

- Add optional saved-progress resume rewind beside Unpause rewind, from 3 seconds to 1 minute. Off by default; included in device setup copies.
- Sort time choices while preserving existing settings and profile values.
- Improve right-edge focus scrolling, Recent Searches artwork and watched/unwatched eye icons.
- All 1,899 Windows tests passed. Update the app and restart Kodi; skin remains 0.1.25. Physical TV verification remains necessary. [Release and validation](docs/release-1.8.111.md).

## What's new in 1.8.110

- Allow delayed first CEC OK repeats and retain safe release-only context dispatch. Raw CEC short taps may wait up to 750 ms; physical Ugoos holds still need verification.
- Remove the Up Next artwork fade and idle prompt, retaining useful source-search status.
- Use a clearer Watch from Beginning icon with a fresh texture filename.
- Restore recent-search dialogs on Back even during the input cooldown after opening a collection.
- All 1,883 Windows automated tests passed. Update the app and restart Kodi; skin remains 0.1.25. [Release and validation](docs/release-1.8.110.md).

## What's new in 1.8.109

- Read missing chapter names from supported playing files without downloading the video or seeking playback. No extra client software is required; unsupported sources keep native/numbered chapters.
- Improve pre-roll fullscreen coverage, HDMI-CEC held OK and native pause-rewind handover.
- Restore collection progress, promote the next episode name in Up Next, and replace the Watch from Beginning icon.
- All 1,878 automated tests passed. Update the app and restart Kodi. Skin remains 0.1.25. Physical remote/audio behaviour still needs verification. [Release and validation](docs/release-1.8.109.md).

## What's new in 1.8.108

- Improve title and episode responsiveness on slower devices, prevent stacked title screens, and protect saved Resume positions.
- Strengthen Play Next handovers and redirected episode metadata; keep late callbacks from cancelling a new request.
- Automatically keep the last ten playback diagnostic reports per device, including redacted Kodi logs, with verified private upload while idle.
- Update the app and restart Kodi. Skin remains 0.1.25. Native Toshiba playback still needs device verification. [Release and validation](docs/release-1.8.108.md).

## What's new in 1.8.107

- Preserve larger redacted Kodi technical logs across restarts and upload verified compressed attachments to your private diagnostic repository.
- Add Play Next/source/progress checkpoints, safe worker/service failure locations and explicit Android crash-buffer access status.
- Measure first/repeat startup through initial Home, catalogue refresh and artwork completion. No per-frame tracing or automatic uploads during playback.
- Update the app and restart Kodi. Skin remains 0.1.25. The Fire TV Play Next crash still requires fresh device evidence. [Release details](docs/release-1.8.107.md).

## What's new in 1.8.106

- Prepare recap rewind while paused, preserving immediate native Play without a later jump.
- Improve pre-roll loading coverage, Atmos matching, stalled-intro recovery and ordinary HDMI-CEC OK playback controls.
- Make portrait cards about 9% larger, fix first-poster clipping and sharpen menu/action icons and poster borders.
- Add safe CEC hold and audio diagnostics. All 1,781 automated tests passed; physical Shield audio and TV-remote behaviour still require verification. Skin remains 0.1.25; restart Kodi after updating. [Release and validation](docs/release-1.8.106.md).

## What's new in 1.8.105

- Keep returns to Search/collections covered until the restored results are ready.
- Start the branded splash earlier and remove unnecessary imports from ordinary launches.
- Let title details become usable before optional ratings, quality fallback and recommendations finish. Preserve episode readiness, focus and source-first quality. Skin remains 0.1.25; restart Kodi after updating. [Release and validation](docs/release-1.8.105.md).

## What's new in 1.8.104

- Fix stuck title loading from Search and collections, retaining the selected results and Back route.
- Add a branded startup splash and bounded recovery when Kodi refuses a window activation.
- Keep native-window retirement and cleanup safeguards. Skin remains 0.1.25; restart Kodi after updating. [Release and audit](docs/release-1.8.104.md).

## What's new in 1.8.103

- Keep the transition from Search/collections covered while stopping trailers and opening movie details.
- Silence repeated hold-Left clicks and restore navigation sounds automatically.
- Show the installed app version in Settings. Skin remains 0.1.25; restart Kodi after updating. [Release details](docs/release-1.8.103.md).

## What's new in 1.8.102

- Improve movie handoffs from Search/collections and loading-card coverage for manual and automatic playback.
- Correct low poster progress fills; use hold Left at the row edge to open the menu on every device.
- Protect slow/startup actions from queued OK presses and keep background updates from changing the selected poster.
- Reject stale worker results, remove duplicate posters and reduce artwork thread creation. Skin remains 0.1.25; restart Kodi after updating. [Release and validation](docs/release-1.8.102.md).

## What's new in 1.8.101

- Move inactive movies and series from Continue Watching to Don't Forget About Me after 30 days; remove their Home cards after another 30 days while keeping progress.
- Watching again resets the clock. Explicit IDs prevent duplicate cards, and moved titles retain their resume/next-episode target and removal action.
- Speed up unchanged Home refreshes and keep cached row order, timezone handling and malformed-state recovery consistent.
- All 1,678 automated tests passed. Skin remains 0.1.25; restart Kodi after updating. [Retention guide](docs/continue-watching-retention.md) · [Audit details](docs/home-retention-audit-2026-10-14.md).

## What's new in 1.8.100

- Include Auto Play profiles and portable playback, subtitle and skip preferences in Shield setup copies.
- Player skin 0.1.25 installs Aerial from Kodi's official repository. Approved profile setup selects it, with backup and Undo; its settings open from Skin Settings / General.
- Give the private setup dashboard Strem4Kodi branding, clearer phone approvals and a manual TV-code entry.
- All 1,661 automated tests passed. Update the Shield and receiving devices, capture a fresh master, then import it on each device including the Shield and restart Kodi. Native Aerial activation still needs a device check. [Setup details](docs/device-setup.md).

## What's new in 1.8.99

- Private profile imports now configure Kodi Home to show Add-ons and Favourites, with category widgets enabled.
- Apply the requested logging, HTTP and local application-control settings and unknown sources, with backup, readback, retry and Undo.
- Fix setup dashboard sign-in behind Caddy without weakening Origin/CSRF checks.
- Player skin 0.1.24. All 1,644 automated tests passed. Restart Kodi, then import your private setup profile to apply these defaults. Native Kodi confirmation prompts remain. [Setup details](docs/device-setup.md).

## What's new in 1.8.98

- Show the next episode title and prepare its sources before the current episode finishes; retain natural-end autoplay and source recovery.
- Preserve progress when Kodi's stop callback exposes a reset clock. Play/Resume now follows the highlighted episode, including unfinished rewatches.
- Keep background progress/recovery running after an optional watcher error; guard slow native-window transitions and clean shutdown.
- Reduce work during search typing and bound hero-cache memory during long browsing sessions.
- Player skin remains 0.1.23. Restart Kodi after updating. All 1,632 automated tests passed; Fire TV card rendering and handoff speed still need a device retest. [Audit details](docs/app-audit-2026-10-14.md).

## What's new in 1.8.97

- Copy preferred S4K settings from your master device through private setup, with a QR code and owner approval on your phone.
- Apply API keys and provider selections with backup, retry and Undo. Stremio account sign-in stays on its official page.
- Existing signed-in devices keep their normal startup; audio/display hardware and custom remote keymaps remain device-specific.
- Start on the Shield: Settings → Account & Stremio → Copy setup profile from this device. Then approve new devices through the setup dashboard. [Setup guide](docs/device-setup.md).
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

## Development

```sh
python -m pip install -r requirements-test.txt
python tools/run-tests.py
python tools/build-stremio-addon.py --output dist
python tools/build-player-skin.py --output dist
```

Use the same Python interpreter for dependency installation and testing. The runner reports its interpreter and Pillow version, and uses the ignored `.test-run-tmp` directory inside the checkout for temporary files. On Windows, it uses Codex's bundled Python if the selected interpreter lacks Pillow and the bundled interpreter is available. Pass unittest discovery options such as `-p test_disk_cache.py` or `-v` to the runner.

Build the update feed using an explicit HTTPS `--feed-url` with `tools/build-kodi-repository.py`. The landing page is generated from the same package versions as the feed, so its download links stay current. App and skin versions must satisfy the declared dependency. Never replace an already published version's package.

[Final release audit](docs/release-audit-2026-10-09.md) · [Upstream review](docs/upstream-review.md)

## Install and configure

Requires **Kodi 21 or later**. Install the repository ZIP, then install Strem4Kodi from **Program add-ons**. The required player skin installs automatically. Restart Kodi after updating both packages.

- [Install / update and current downloads](https://daanvb.github.io/strem4kodi-repository/)
- TV installation: add `https://daanvb.github.io/strem4kodi-repository/` in Kodi's
  File manager, then Install from zip file → that source → `repository.strem4kodi.zip`.
- [Configuration guide](docs/configuration.md)
- [New lists, categories and Discover](docs/discovery.md)
- [Shared format / logo database](docs/format-database.md)
- [Audio pre-roll uploads](https://github.com/daanvb/strem4kodi-repository/tree/main/prerolls)
- [Full changelog](changelog.txt) and [earlier release highlights](docs/release-highlights.md)

## Repository roles

| Repository | Purpose |
| --- | --- |
| [Private development source](https://github.com/daanvb/Stremio-for-Kodi-private/tree/strem4kodi) | Active code, tests and build tools on `strem4kodi`. Access required. |
| [Public installation feed](https://github.com/daanvb/strem4kodi-repository) | Kodi update packages, installation guide and public pre-roll release assets. |

The live feed retains the current release and one previous version for rollback. Earlier packages remain in Git history. See [repository layout and maintenance](docs/repository-layout.md).

## Credits and licence

Based on [Stremio-for-Kodi](https://github.com/0eroiQ/Stremio-for-Kodi), with Nimbus layouts/artwork credited to Ivar Brandt. Original contributor credits, third-party notices and **GPL-2.0-or-later** are retained. See [full acknowledgements](docs/configuration.md#source-builds-and-credits) and [LICENSE](LICENSE).

Strem4Kodi is an independent community project, not endorsed by Kodi or Stremio. It uses the TMDB API but is not endorsed or certified by TMDB.
