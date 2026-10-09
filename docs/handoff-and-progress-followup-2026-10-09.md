# Playback handoff and white progress tracks — 9 October 2026

Included in app 1.8.55. Player skin remains 0.1.16.

The follow-up device report measured 0.45 seconds finding a suitable source,
17.33 seconds preparing it and 5.60 seconds opening/buffering in Kodi, for
23.38 seconds overall. Preparation included 13.74 seconds before playback
dispatch, 3.44 seconds waiting for the resolver, 0.05 seconds on details/context
and 0.10 seconds on subtitles. Subtitles do not explain this attempt's delay.

The largest segment still combined loading-card handover and stream-cache
persistence; the report did not prove which operation caused that delay. An
avoidable cost was identified in the code: app playback loaded the shared stream
cache, copied its saved URLs, added the current source and saved the entire cache
through account storage, including its shared writer mutex and durable write.
Older sources and metadata therefore increased the work needed for a new play.

App playback now writes one independent owner-only request file, then dispatches
the existing resolver. It uses an atomic replace without durable fsync because
this is temporary process handoff, not account persistence. Account and source
caches remain unchanged. Concurrent requests retain independent keys, resume
offsets, attempts and metadata. Old links still use the legacy stream cache;
broken new requests fail rather than silently selecting a legacy source.
The resolver retains its one-hour expiry and direct-source validation. Progress,
successful-source learning, subtitles, pre-rolls and Up Next use the same request
lookup. Expired files are pruned after dispatch on a background thread. Native
Kodi connection/buffering is unchanged; faster device startup is not established
by the local tests.

The report now divides handoff into loading-card handover, adapter setup, request
save and pre-roll selection/dispatch. It still records no title names or URLs,
and no elapsed timer is shown on the loading card.

The previous poster fix did not remove the white line on the user's device. All
six poster/episode progress layouts now draw the dark track as a separate image
at exactly the fill's coordinates and dimensions. The progress control has
transparent background/overlay assets, with the theme accent on the control
itself. The same local capsule supplies the fill; reveal scaling is disabled so
the fill stretches with the percentage. Control-level tint is compiled for all
five themes. Native progress values, visibility and focus are unchanged.
This follows the [Kodi progress-control implementation](https://github.com/xbmc/xbmc/blob/Omega/xbmc/guilib/GUIProgressControl.cpp)
and its [texture configuration](https://kodi.wiki/view/Progress_Control).

Validation: 1,128 tests passed. New tests deliberately hold the account writer
lock during handoff, check concurrent request isolation, cancellation before
dispatch, legacy links, malformed keys/payloads and expiry cleanup. Progress
checks cover every layout in all five themes, including real transparency and
track/fill alignment. Package integrity/source agreement, Python/XML parsing and
credential signatures checked. Native rendering and a new device timing report
remain necessary to verify the visible and speed improvements.
