# Loading and UI follow-up — 9 October 2026

Automatic movie/series/animation selection now treats Any quality as 1080p first,
then 720p and lower resolutions, then unreported quality, with 4K as a last resort.
Explicit 4K preferences remain supported. Device quality ceilings, saved picker
filters, failed-source exclusions and automatic retry limits still apply. This
policy also applies to completed-search selection and Up Next, not just early
results. A previous UHD release does not override available HD under Any; the
resume position is retained when changing sources.

An exact 1080p match can start from the first usable arrival. With a 720p ceiling,
720p is the early target. Lower-resolution or 4K fallbacks wait for completion to
avoid selecting them while an HD result is still pending. Explicit provider or
file-size ordering waits for all add-ons. The old one-second settling timer has
been removed; playback still runs outside the provider callback. URLs/release
duplicates do not need to accumulate before starting a suitable source.

In automatic mode, selecting an episode opens the title loading card immediately.
The source picker stays hidden during the search. The card hands over to the
playback loading card without exposing source rows, and keeps its existing local
trivia and artwork. Search failures reveal the manual picker with Retry. Back or
Cancel invalidates late replies and scheduled playback; cancellation during the
handover is bound to that playback attempt. Manual selection still opens the
ordinary source picker. Existing source caches/shared searches are reused; no
additional speculative stream searches or video downloads are introduced.

Settings use static green/red health text in both focused and unfocused layouts,
avoiding unreliable dynamic list-item text colours. Direct actions have no
submenu chevron. Discover/Library filter labels reserve space for dropdown arrows;
Library Refresh has no dropdown arrow. Ratings reserve enough width for 100%.
Favourites/Watch Later use the same poster treatment as Home: redundant outer
captions are hidden instead of being clipped below the poster viewport. Selected
title details remain in the hero. Settings help previews use the app's smaller
readable font; Info still provides the complete text. More actions uses the
existing illustrated action menu, and Cancel uses a solid rounded focus pill.

This is app version 1.8.51; the companion skin remains 0.1.15. Local tests and
package checks can validate selection, cancellation and geometry, but a Kodi TV
device is needed to confirm remote focus and startup times.

Validation: all 1,088 app tests passed. The 1.8.51 ZIP passed integrity checks,
byte-for-byte source agreement, parsing of 177 Python and 162 XML files, and
credential-signature checks. The source credential audit also passed. The bundle
is prepared for the 1.8.51 release through the public Kodi update feed.
