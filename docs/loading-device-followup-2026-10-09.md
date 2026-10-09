# Loading and troubleshooting follow-up — 9 October 2026

Release: app 1.8.53 with companion skin 0.1.16; the app requires the updated skin.

The device photographs showed that the previous modal-loop change did not solve
input ownership or the blank first frame. The old dialog was constructed on the
parent callback thread, and doModal was entered before that callback returned.
Kodi dispatches Python callbacks while holding the native object's lock and binds
callbacks to the Python thread that constructed the object. Provider workers could
therefore wait on the parent window while Cancel needed the same work to finish.
Immediate-return dialog mocks did not exercise this behavior.

The dialog now constructs and pumps its modal loop on one lasting dedicated
thread. The parent callback returns after scheduling the search. Initial text,
artwork and available local title facts are compiled into the XML before native
allocation, and search hands over to playback on the same dialog instance. No
extra trivia lookup is introduced. Cancel closes the dialog before parent cleanup,
signals an attempt-bound cancellation token, and prevents a late source from
starting or reopening the card. Cleanup runs outside the native input callback.
The companion skin suppresses its duplicate busy dimming/spinner while the app's
loading dialog owns the wait; ordinary Kodi busy artwork remains available.

Kodi source references: [callback thread ownership](https://github.com/xbmc/xbmc/blob/Omega/xbmc/interfaces/python/CallbackHandler.cpp),
[native object locking during callback dispatch](https://github.com/xbmc/xbmc/blob/Omega/xbmc/interfaces/legacy/CallbackHandler.cpp),
and [modal callback pumping](https://github.com/xbmc/xbmc/blob/Omega/xbmc/interfaces/legacy/Window.cpp).

The RecoveryPlayer listener is constructed on the lasting media-window thread
rather than a short-lived early-selection timer. A previous trailer's queued
Stop/End cannot discard a new, unstarted attempt. Hidden detail-page refreshes
are deferred during loading and playback, and Back no longer synchronously
reloads account/resume data. Repeated Back presses during asynchronous Stop are
guarded; the configured Back behavior is retained. The cancellation message sits
beside the episode selectors, above the posters.

App-owned playback skips the extra media GET preflight and lets Kodi make the
media connection. Direct known provider error videos are still rejected, and
legacy playback routes retain the bounded preflight. Existing failure recovery,
quality limits, exact early source selection and the two-second resume grace are
retained. This removes redundant work but does not establish a device-specific
speed gain or explain the entire reported 25-second wait. A local Last playback
loading report separates source search, preparation and Kodi opening/buffering;
it records no title names or source URLs and adds no timer to the loading card.

Provider diagnostics now hydrate saved history before recording the first new
request. Saves merge newer summaries and retry a concurrent snapshot conflict,
so one resolver does not erase another provider's history. Troubleshooting lists
every enabled stream-capable provider, including PenguPlay and Usenet Ultimate,
even when no summary exists. It explains provider restrictions and cached source
reuse. These rows are read-only; viewing them sends no health-test requests or
provider searches. Missing history is not presented as a provider failure.

Validation includes real threaded, blocking modal test doubles, Cancel while the
parent lock is busy, cancellation during construction/handover, stale dialog
ownership, first-frame content, provider-history restart/concurrent saves,
enabled-provider visibility, source preflight and repeated Back races. Actual
Kodi remote input, skin rendering and network/player timing still require device
verification; automated tests do not certify those outcomes.

Final local validation: 1,113 automated tests passed. The app and companion skin
preview archives passed integrity, byte-for-byte source agreement and credential
signature checks. Source parsing passed for 331 Python and 283 XML files, and Git
whitespace checks passed. The previews are isolated under dist/loading-thread-preview;
their version labels remain the published versions and they are not release builds.
Release packages use app 1.8.53 and companion skin 0.1.16, with the matching required dependency. Both packages must be updated before restarting Kodi.
