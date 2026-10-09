# Continuous autoplay loading — 9 October 2026

The automatic search and playback stages now use one dialog instance. The search
starts with the existing title artwork and locally available trivia or title
facts. When a suitable source is chosen, the same card changes from Finding your
stream to Starting playback. No second layout compilation, second open animation
or source-list flash is needed. Titles without factual local data omit the trivia
strip; loading never performs a trivia network request.

The calling UI thread enters Kodi's doModal loop after launching the asynchronous
search. This gives the loading dialog input ownership and processes Cancel/Back
callbacks while provider requests run. A manual source selection also enters that
loop during player startup. The dialog now fills its own label, textbox, image and
visibility controls, rather than relying on unqualified Window.Property lookups
that can refer to the media window underneath a dialog. The live Cancel callback
follows the same dialog from the search token to the playback attempt. Stale
callbacks, dismissed windows, cancelled grace timers and late replies are guarded.

Kodi reference: [Window.doModal and callback dispatch](https://github.com/xbmc/xbmc/blob/Omega/xbmc/interfaces/legacy/Window.cpp)
and [dialog opening implementation](https://github.com/xbmc/xbmc/blob/Omega/xbmc/interfaces/legacy/WindowDialogMixin.cpp).

On resume, a cached or already-arrived working release remains the first choice
subject to the existing quality ceiling, filters and HD policy. If it is absent,
the first exact suitable alternative starts a two-second grace period. Arrivals
do not extend that deadline. The previous release starts immediately if it arrives
during the grace; otherwise the best exact alternative available at expiry starts
with the saved playback position. Completed searches use their existing selection
without waiting out an unnecessary grace. New playback gets no added delay. The
grace is built-in behavior, not an additional user setting. Explicit provider or
file-size ordering still needs the complete search.

Source arrivals reach automatic selection before availability database persistence.
Hidden poster badge refreshes are skipped on the automatic search path. The
best-effort error-video preflight uses a three-second network timeout rather than
eight seconds; timeouts remain inconclusive and defer to Kodi. Direct provider
error videos, detected error redirects and structured provider errors are still
rejected. Live streams remain exempt from the extra probe. This does not reduce
Kodi's actual playback/buffering timeout or add provider searches.

Automated validation covers direct dialog content and trivia in both stages,
single-window reuse, live and stale cancellation, resume-position preservation,
the bounded grace and earlier working-release arrival, cache persistence failure,
existing source/quality rules and error-video detection. A real Kodi device is
still needed to confirm remote behavior and measure provider/player startup time.
These changes are included in app version 1.8.52. The companion skin remains 0.1.15.

Validation: all 1,095 automated tests passed. The local preview ZIP passed archive
integrity, byte-for-byte source agreement, parsing of 177 Python and 162 XML files,
and loading-dialog control checks. The source credential-signature audit and Git
whitespace checks passed. The preview is isolated from published release packages.
