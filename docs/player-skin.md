# Strem4Kodi Player companion skin

This Kodi 21/Omega companion skin supplies Strem4Kodi playback controls.
Repository installation installs it automatically as an app dependency; choosing
it as the active Kodi skin remains optional. The first version keeps Estuary's other
screens and native audio, subtitle, video, PVR and accessibility settings.

## Install and activate

1. Update Strem4Kodi to **1.8.17** through **Strem4Kodi Repository** on Kodi 21 or later. Kodi installs the companion skin automatically.
2. Restart Kodi so the updated playback service reloads.
3. Open **Strem4Kodi Settings > Appearance > Player appearance**, then select **Strem4Kodi Player** under Kodi **Interface > Skin**.
4. Play a title through Strem4Kodi. Open playback controls with your remote.

For direct ZIP installation, install `skin.strem4kodi-0.1.5.zip` first, then
`script.strem4kodi-1.8.17.zip`, using Kodi’s **Install from zip file**.

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
duration and a smoothed finish estimate. Four labelled buttons keep the main
bar simple: Play/Pause, Audio, Subtitles and Settings. The seek bar uses Kodi's
seek action. Audio and Subtitles open matching two-line track pickers with the
current choice marked. Subtitles includes Off, Download subtitles and access
to Kodi's advanced subtitle settings, even if the file has no embedded tracks.
Settings groups audio adjustments, subtitle settings, picture settings and
Stop playback into one menu. Back cancels each picker without changing tracks.
Selections are discarded if playback moves to another file while a menu is open.

## Chapters

During playback, open **Settings > Chapters** to see the file's chapter names and
start times and jump to a chapter. The matching chapter/bookmark dialog uses Kodi's
native chapter handling, including its current-position selection, on Kodi 21.
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

Under **Subtitles & AI**, **Start with subtitles off** defaults to on for videos
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
Explicit AI subtitle mode takes priority over forced-only automation. The manual
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
