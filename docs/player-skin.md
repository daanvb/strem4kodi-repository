# Strem4Kodi Player companion skin

This Kodi 21/Omega companion skin supplies Strem4Kodi playback controls.
Repository installation installs it automatically as an app dependency; choosing
it as the active Kodi skin remains optional. The first version keeps Estuary's other
screens and native audio, subtitle, video, PVR and accessibility settings.

## Install and activate

1. Update Strem4Kodi to **1.8.30** through **Strem4Kodi Repository** on Kodi 21 or later. Kodi installs the companion skin automatically.
2. Restart Kodi so the updated playback service reloads.
3. Open **Strem4Kodi Settings > Appearance > Player appearance**, then select **Strem4Kodi Player** under Kodi **Interface > Skin**.
4. Play a title through Strem4Kodi. Open playback controls with your remote.

For direct ZIP installation, install `skin.strem4kodi-0.1.14.zip` first, then
`script.strem4kodi-1.8.30.zip`, using Kodi’s **Install from zip file**.

You can return to your previous skin through the same Kodi setting. Installing
the ZIP does not silently change your skin. Normal Kodi playback uses the
original Estuary controls; identified Strem4Kodi playback uses the new bar.
Strem4Kodi's existing loading, Skip Intro and Up Next overlays remain in use.
This version does not replace Kodi's home screen with the Strem4Kodi app.

## Automatic installation from the repository

The app declares `skin.strem4kodi` as a required dependency. The repository feed
includes both ZIPs and their metadata, so Kodi resolves and installs the skin
when installing or updating Strem4Kodi. Kodi manages future updates normally.
The skin does not declare a dependency on the app, avoiding a dependency loop;
it uses Estuary controls when Strem4Kodi playback properties are unavailable.
The companion requires Kodi 21/Omega's GUI version, so this release requires
Kodi 21 or later. On older Kodi versions the dependency cannot be installed.

Activation is a separate user choice under **Strem4Kodi Settings > Appearance >
Player appearance**, which opens Kodi's Interface settings. The app does not
silently switch Kodi's global skin or modify its installed skin files.
Both packages are included in the published repository feed.

## Controls and audio

The bar shows the title, series/episode information, active audio, elapsed time,
duration and a smoothed finish estimate. Five labelled buttons keep the main
bar simple: Play/Pause, Audio, Subtitles, Settings and Media info. The seek bar uses Kodi's
seek action. Audio and Subtitles open matching two-line track pickers with the
current choice marked. Subtitles includes Off, Download subtitles and access
to Kodi's advanced subtitle settings, even if the file has no embedded tracks.
Settings contains Chapters, ChaptersDB edition selection, Smart credits and picture settings. Back cancels each picker without changing tracks.
Selections are discarded if playback moves to another file while a menu is open.

## Chapters

During playback, open **Settings > Chapters** to see the file's chapter names and
start times and jump to a chapter. The Strem4Kodi chapter picker uses the same positions as the timeline and selects the current chapter on opening. It does not open Kodi's bookmarks menu.
Saved Kodi bookmarks may also appear in the list; its bookmark buttons retain
their normal Kodi behavior and local storage.

Embedded chapters come from the playing file or stream and always take priority.
If there are none, **ChaptersDB fallback** in Strem4Kodi Playback settings adds an
on-demand lookup for titles identified by IMDb. For series, the season and episode
must match exactly. Choose the matching edition, then a chapter. Lists with
invalid, unordered or out-of-range times are rejected; those checks do not prove
that an edition matches your release. There is no automatic rescaling of timings.

ChaptersDB requests are anonymous, bounded and cached locally for 24 hours in
`chaptersdb-cache`. Only title identifiers are sent, not stream URLs or account
keys. Availability varies; the live API examples tested returned no approved
entries. Missing entries and network failures leave playback untouched. Turn the
fallback off to use embedded chapters only. This does not change IntroDB or smart
credits, inspect the stream externally or download the full video.

## Forced subtitles

Under **Subtitles**, **Start with subtitles off** defaults to on for videos
started through Strem4Kodi. The service disables inherited full-subtitle defaults
when it first observes playback. Manually opening the subtitle picker takes
priority, and full subtitles can be enabled there. Other Kodi videos are unaffected.

**Automatic forced subtitles** defaults to embedded tracks, then matching addon
download. Use Off or Embedded tracks only to change this. **Forced subtitle
language** defaults to English; optionally follow Kodi's preferred language.
The service prefers matching tracks flagged forced or explicitly named forced.
After allowing ten seconds for embedded tracks, it can query your enabled Stremio
subtitle addons in the background. Only explicitly forced results tied to the
exact selected release filename are downloaded automatically. At most two files
are tried, with existing size/type validation, and a changed episode or manual
subtitle choice cancels application. Missing forced flags or release details means
no automatic download; use manual subtitle search instead.

This identifies metadata marked as forced, not foreign dialogue by analysing the
audio. It cannot reliably detect a need for subtitles when no such metadata exists.
The manual
Download subtitles entry opens Kodi's subtitle-service search; automatic forced
downloads use Stremio subtitle addons, whose metadata supports the checks above.

Language, codec and channels come from Kodi's active track, not the stream
provider's release name. AC-3 becomes Dolby Digital; E-AC-3 becomes Dolby Digital
Plus; TrueHD becomes Dolby TrueHD. Atmos/DTS:X appear as detected formats only
when Kodi explicitly reports the matching codec extension. Track names remain
labelled **Track:**; an “Atmos” track title is not verification of Atmos.
Some Kodi/platform combinations report only the base codec. Unknown languages
and formats are shown honestly rather than defaulting to English or Atmos.
This describes the selected source track, not the format received by an AVR
after decoding, downmixing or passthrough. Playback/output settings are unchanged.

The service checks audio once per second while the control bar is visible.
After selecting a track, its new information appears on the next service tick.
No network inspection or file download is used. Seeking, pauses and buffering
adjust the finish estimate; differences of up to two seconds are held steady to
avoid minute-boundary flicker. Unknown-duration streams omit the estimate.

Configure auto-hide under **Strem4Kodi Settings > Playback**. The default is
five seconds; pause, seeking and open submenus keep the controls available.

## Build and verification

The complete skin sources are in `companion/skin.strem4kodi`. Build with:

```text
python tools/build-player-skin.py --output dist
python tools/build-stremio-addon.py --output dist
```

The app builder excludes the companion directory. Each ZIP is a separate addon;
the app declares the companion skin as a dependency. Source attribution and
licenses are retained. Baseline: Kodi's Estuary from the Omega branch at commit
`f8815ee40f49a700c047982d752be4b2a61420e2`.

Automated checks cover active audio names, track indices, cancel/episode-change
handling, playback ownership, finish-time jitter and packaging/XML navigation.
A Kodi device test is still required for actual rendering, focus, skin switching,
audio/subtitle dialogs, seek/pause, live streams and the existing playback overlays.
The supplied design preview is a static rendering of the layout, not a Kodi
runtime screenshot. This preview has not been published to the update feed.

Build a complete feed with `tools/build-kodi-repository.py --package <app.zip>
--skin-package <skin.zip> --output <feed-directory> --feed-url <https-base-url>`.
The builder rejects stale skin versions and circular app/skin dependencies before
writing the feed. If `--skin-package` is omitted, it builds the checked-in skin.

## Media info

Open **Media info** on the playback bar, or **Settings > Media info**. The
two columns separate Kodi-detected video/audio details from unverified source
claims. Use Up/Down to scroll, Left/Right to switch columns, and Back to close.
The panel closes if playback stops or changes to another file.

Resolution, codec, frame rate, dynamic range, pixel format, decoder, audio
language/format, sample rate and subtitle status are shown when available.
Kodi 22 adds `VideoPlayer.HdrDetail`, allowing Dolby Vision profiles and FEL/MEL
to appear when Kodi reports them. Kodi 21 still shows the rest of the panel;
unavailable fields say so. A FEL label does not prove enhancement-layer
processing on the device. This reads playback metadata without downloading or
probing the media file. Details are a snapshot when the panel opens.

Small format logos accompany the detected metadata. Dolby Atmos is shown only
when Kodi reports an Atmos codec extension for the current audio format; a
track name or release title alone cannot enable it. Unsupported formats retain
readable text. Asset provenance is recorded alongside the bundled logos.

## Seek bar and chapter access

The seek line is 14 pixels high, with taller contrasting chapter ticks for
embedded chapters. The playback and temporary seek bars use the same styling;
the seek thumb remains centred on the line. The current chapter number/title
appears above the line when supplied by the file.

From the player buttons, **Up** focuses the timeline in **Scrub** mode.
**Up again** enters **Chapters** on the same timeline when embedded chapters
are available. Left/Right highlights a chapter marker and previews its name and
start time. Playback continues unchanged until **OK** jumps. **Down** returns
to Scrub; another Down returns to the buttons. **Back** cancels and closes the
controls. The white selection marker and explicit mode/help text distinguish
chapter selection from normal seeking. No double-press timing is required.

Kodi 22 supplies all chapter names through `Player.GetChapters`. Kodi 21 uses
its native chapter positions and the current chapter name; other names appear
as Chapter 1, Chapter 2, etc., with start times. Titles are never discovered by
seeking through the file. Videos without embedded chapters stay in Scrub mode
on the second Up. ChaptersDB lookup remains under **Settings > Chapters** and
is a separate release-specific list; it does not create embedded timeline
markers. The selector closes on stop or a different playing file, and checks
that playback is still the same before jumping.


ChaptersDB edition choices now show **Possible match**, **Unverified**, or
**Low confidence**, with the supporting release clues. Edition notes are
compared with the selected stream filename for explicit cut/source wording.
An explicitly labelled runtime in the note can be compared with Kodi's actual
playback duration. ChaptersDB does not advertise a dedicated edition-runtime
field; absent notes remain unverified. A final chapter start is never treated
as the runtime. All valid editions remain selectable and require a manual
choice; matching does not rescale chapter times or verify the cut. Codec,
Dolby Vision and audio format do not establish edition identity.


Idle hiding covers both the main control menu and the separate seek-feedback bar.
When the configured inactivity period expires, an idle scrub slider relinquishes
focus before the menu closes. Retained seeking/show-time flags cannot keep our
feedback visible indefinitely. New remote input, a pause, buffering or a new
video clears the suppression. Recent actual seeks extend the timeout; open
Audio, Subtitles, Settings, chapter selection and other modal menus are left
alone. Kodi default retains Kodi's own hiding behaviour.

Trailer previews and the Trailer button use the same cancellable hero playback route. If Kodi opens fullscreen during an owned preview, the app returns it to the original browsing window while leaving unrelated video, navigation and open player dialogs alone. This needs a device check on Kodi.

With Strem4Kodi video playing in the companion skin, Up does nothing while the playback controls are closed. Press OK to open controls, then Up for scrubbing and Up again for chapter selection. The fullscreen chapter/large-forward-jump shortcut is suppressed only for owned custom-player video; live TV and other playback retain Kodi behaviour. Left, Right and Down retain their existing bindings. The navigation keymap is installed when opening Strem4Kodi, independently of the Back preference.

The second Up press is handled explicitly while the scrub bar has focus. Settings > Chapters provides a separate chapter list. Controls also time out when Kodi reports them as modeless; open options and chapter menus remain visible until dismissed.

## Resume source memory

With automatic source selection, Resume first tries the last successful source for that exact movie or episode. Success requires five seconds of real advancing playback, not just opening a source or seeking to the saved position. The matching source must still appear in current results and pass active filters and the maximum quality limit. Manual selection remains manual; recommended selection highlights the remembered source. Play from Beginning and a different episode keep normal ranking.

Memory stores hashed source/release fingerprints on this device, never reusable playback URLs. A changed URL can match an unambiguous filename from the same provider. Missing, ambiguous or failed matches fall back to normal ranking and the existing bounded retry flow. Records expire after 30 days and are limited to 500 titles/episodes.

### Remote scrubbing (player skin 0.1.7)

Left/Right during playback or Up from the player buttons opens a preview on the
timeline. Each tap moves ten seconds. Repeated presses accumulate a single skip;
holding accelerates to thirty, then sixty seconds per repeat. The marker and label
show the destination and total offset. Playback seeks once after 400 ms without
directional input, or immediately on OK. A single worker handles seeks away from
the input handler, keeping the controls responsive while a source catches up.

Back cancels any pending jump and closes the controls. Down cancels any pending
jump and returns to the buttons. Up cancels the preview and enters chapter
selection. Scrub controls obey the configured auto-hide timeout and remain visible
while paused or buffering. Other skins and live TV keep Kodi's native shortcuts.
Stream buffering and keyframe accuracy still depend on the source and Kodi.

### Mark missing credits

The episode player has a small round Credits start button with a three-line animated crawl icon at the far right of the
control row. One press saves the current position without a menu. Holding
OK/Enter during episode playback opens a menu to mark or manage smart credits.
For that menu, the position is captured when it opens, so time spent choosing
the option does not move the marker. This is
an explicit episode marker, not video analysis. A valid IntroDB marker takes
priority. Otherwise the saved marker is used for the same episode when its
runtime matches within five seconds; it also contributes to the series estimate
for other episodes after three consistent samples. Automatic observations do
not overwrite manual markers. Marking again corrects the saved position.

Markers use the existing private smart-credits sync when enabled. Each series
retains the latest 24 samples, including manual markers. The action requires
Strem4Kodi episode context matching the currently playing file, and a sensible
closing-credits position (in the latter half, 20 seconds to ten minutes before
the end, no more than 35% of runtime). It does not skip or stop the video.

### Scrub confirmation and audio badges

Settings > Playback > Scrub seek confirmation chooses Seek on release (the
existing default) or Press OK to seek. In OK mode, releasing Left/Right leaves
the preview in place so it can be adjusted before confirming. Back cancels it.
Holding Left/Right is throttled to one move per 150 ms; steps start at ten seconds,
increase to twenty after three seconds, then forty after six seconds.

The preview shows Jump to followed by the destination time, with Forward/Back
and the total change underneath. Preview only means playback has not moved.
A solid bottom panel replaces the underlying controls while scrubbing. Two short
help lines explain movement, confirmation, chapters and cancelling the preview.
Player Settings lists Chapters, Use ChaptersDB instead and Smart credits first,
when available, followed by Picture settings and Stop playback. Audio, Subtitles
and Media Info remain on their dedicated player buttons without duplicate entries.

Media Info refreshes detected audio while open. Known aliases and combined
Dolby Digital Plus/Atmos labels resolve to the selected track's base-format
badge plus Atmos when Kodi reports it. Missing RPC codec data can use Kodi's
active audio codec label. A track title or filename claiming Atmos does not
count as detected Atmos, and conflicting codec families do not enrich one
another during track changes.

### Correcting smart credits

Open player Settings > Smart credits, or an episode's More > Manage Smart Credits
for This Series. Ignore that episode's timing, review and remove individual
IntroDB/manual samples, or clear every known sample for the series. Clearing
samples keeps the series timing override. Ignored episodes are not automatically
relearned, and their IntroDB credits timing is ignored for Up Next. Mark Credits
start here again to supply a replacement. IntroDB skip buttons are separate.

Removals sync as timestamped deletion records, preventing an offline device on
this version from restoring an older sample. The latest 24 live samples are
retained separately from deletion records. Estimates measure credits length
backwards from the end, rather than copying an absolute start position. They
prefer the same season and comparable runtimes, require three agreeing samples
and at least 75% agreement within 20 seconds or 25% of the typical credits length.
Otherwise the configured fallback is used; actual episode markers are preferred.

The hold-OK shortcut applies only to Strem4Kodi episodes in its companion skin.
Short OK presses retain their normal controls/selection behavior, and nested
audio, subtitle and chapter dialogs retain their own navigation. Kodi normally
uses keyboard hold-Enter/OK for Play/Pause in fullscreen playback; other media
and skins keep that fallback. Remote support depends on whether the device sends
an input Kodi recognizes as a long press. The visible button remains available
when a remote has its own hold action or does not report long presses.

### Episode watched threshold

Episodes count as watched after 85% of their runtime has actually played across
resumes. Seeking past sections does not add viewing time. They also count as
watched when a Skip Outro card is shown, when any credits-time Up Next card is
shown (including estimates, series overrides and fallback timing), or when a
valid Credits start marker is saved. Skip Intro and recap cards do not count.
The credits event is bound to the active episode and stream, queued immediately
through the existing progress retry queue, and retained through playback stop.
While playing, the resume position is kept; stopping after that event clears
the current episode's resume and points to its next available episode. Movie
viewing thresholds remain unchanged. Removing a credits sample changes timing
and learning; use Mark as unwatched separately to reverse its watched status.

### Choose online chapters explicitly

Player Settings > Use ChaptersDB instead opens the online edition picker even
when embedded chapters are available. Choose an edition, then select a named
chapter to jump. This explicit lookup is also available when automatic ChaptersDB
fallback is off. Names and timings come from the submitted list; English names
are not guaranteed. Normal chapter navigation continues to prefer embedded
chapters, and a changed playback session cancels the online selection.

### Episode presentation and format artwork

The custom player shows an episode title and synopsis card at the upper right
while its controls are open. It follows the same visibility and idle behaviour
as the controls and is hidden during scrubbing or another player menu. Movies
and episodes without a synopsis do not show an empty card. The details hero
uses a separate episode-title line with an eight-pixel gap before the synopsis.

Media Info uses the Dolby Vision Horizontal logo and sharper original TrueHD
and Digital Plus artwork, with light tiles for black logos and preserved aspect
ratios. Atmos retains the original Dolby logo. Other formats retain Estuary
flags. All logo choices still follow Kodi's detected format and active audio
track; a source filename alone cannot enable Dolby Vision or Atmos.

In 1.8.30 / Player skin 0.1.11, the normal timeline matches scrub and chapter selection. Synopsis previews use episode text when supplied, remain static, and end at a word boundary. Format badges share aligned sizing and preserve original logo proportions and colour artwork.

In 1.8.31 / Player skin 0.1.12: normal and feedback timelines explicitly override native progress borders and disabled-slider artwork. Both use the same filled cyan track and slim white position marker as scrub mode. Feedback without buttons has a compact panel and an OK hint for opening player controls. Media info and browsing use locally bundled transparent logo variants, with no light backing tiles.

### Local chapter labels and softer overlays

Common numbered chapter labels and opening/credits labels translate to English locally, including Russian, Ukrainian, French, German, Spanish, Portuguese, Italian, Dutch, Polish, Greek, Chinese, Japanese and Korean numbered labels. This is a small offline dictionary, not full scene-title translation: unknown titles remain unchanged. Display translation does not alter chapter times. The player, chapter picker and timeline use the same translations.

Player overlays now blend into the picture with a transparent upper gradient; scrub and chapter panels fade in and out. Format artwork uses smaller display slots and newly bundled renderings. Browsing availability badges appear at the lower right above the title rows, including unwatched focused titles after a background source check.

In 1.8.33 / Player skin 0.1.14: Offline Lanczos-filtered, display-sized transparent format logos preserve HDR10+ and DTS colour artwork. The owned fullscreen Left/Right shortcuts enter custom scrub; Down opens player controls. Native seek feedback is hidden during owned playback and underlying video OSD closes before custom scrub/chapter panels, avoiding menu flashes during mode changes. Other skins and live TV retain their native shortcuts. Movie heroes show a clock and full-runtime finish estimate, refreshed each minute. The first eight titles on a browsing page warm source availability serially, alongside a faster debounced focused-title check; checks share source-cache locks and stop when the page changes. Provider response time still determines when new badges appear.

Pending availability optimisation: a separate persistent badge-only cache retains movie and exact-episode summaries across provider configuration changes, without retaining playable URLs in that cache. Known badges display immediately for up to seven days while summaries older than one hour refresh in the background. Changed episode progress uses a distinct context. Page warming covers all loaded rows in interleaved order with two background workers and focused-title priority, stopping obsolete page requests. Playback source URLs retain their existing shorter freshness and provider checks. A first-ever lookup still depends on provider response time; missing format reports cannot be invented.
