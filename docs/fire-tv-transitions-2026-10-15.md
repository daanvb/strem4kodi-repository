# Fire TV search and movie startup

Unpublished changes following the Fire Stick 4K report. No physical device was
attached for reproduction, so these are fixes for identified lifecycle risks;
automated tests do not establish the device outcome.

Search already closes its full browsing window before opening movie details to
avoid retaining two poster-heavy native windows. The shell now keeps the old
native owner alive until Kodi no longer reports it as active or visible, before
releasing it and allocating the next window. The same retirement boundary is
applied when returning from details to Search. A two-second retirement timeout
stops further window allocation and records the stage in private diagnostics.
Handover uses the registered owner ID, rather than a transient active window ID.
Following clarification, Discover collection/catalogue grids use this shell
handover too. Their exact list, selection, filters and Back origin are restored,
including saved collections opened from Favourites/Watch Later. Watched-card
refresh and the load-more card are preserved when rebuilding a collection.

Both manual and automatic source dispatch now run off the input callback. They
wait for the existing loading card's onInit and a rendering interval before
dispatching playback. Cancellation, a replaced attempt or failed card creation
prevents that dispatch. No extra source probe is added for manual playback.

The source-opened callback no longer dismisses the card. AV readiness closes it
when fullscreen video is visible, with the existing bounded fallback for skins
that require the modal to close first. If the AV callback is missed, fallback
readiness requires video time beyond the resume position and no native busy
dialog; fullscreen alone is insufficient. Existing automatic provider-error
validation and pre-roll gap covering are retained.

Regression checks exercise retained native ownership during a queued close,
visible-but-inactive windows, stuck retirement, slow loading-card initialisation,
late initialisation after cancellation, manual opening before AV readiness,
source-dispatch errors, and a fullscreen window before decoder readiness.

Device checks after release: open a movie from both typing suggestions and full
Search results; navigate and return to the same results; manually and
automatically start both a normal movie and a large Dolby Vision source; cancel
during loading; stop or skip a pre-roll; check recovery from a failed source.
These changes do not change Dolby Vision decoding support or device codecs.
