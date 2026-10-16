# Strem4Kodi 1.8.109

- Read missing chapter names directly from supported MKV/WebM and MP4 files in the background. Prefer Kodi's full chapter API, retain native jump times, validate the exact source/runtime/markers, bound range reads and cache results locally. No extra client software is required; unsupported containers and servers retain native/numbered chapters.
- Keep the pre-roll handover covered until fullscreen video becomes active, requesting fullscreen once instead of dismissing the cover on a two-second timer.
- Handle raw HDMI-CEC/IR OK repeats within S4K browsing windows: one normal selection after release, or one context menu after a hold. Preserve ordinary keyboard/Android and fullscreen playback controls.
- Prepare pause-rewind without seeking the paused decoder. Dispatch one native relative scrub immediately on resume, with source/session/manual-seek guards and no delayed retries.
- Restore progress overlays for temporary Continue Watching entries in collections, and refresh both search and TMDB collections on return. Use the next episode name as the Up Next card's main title and replace the Watch from Beginning icon.
- All 1,878 automated tests passed on Windows. Exact-source CI, package/source consistency, Python 3.8 syntax, XML, ZIP integrity, credentials, feed and live downloads are separately checked before publication. Physical CEC timing, pre-roll transitions and passthrough audio sync still require device verification.
- Player skin remains 0.1.25 and repository installer remains 1.0.4. Update the app and restart Kodi.

Chapter discovery waits for five seconds of stable owned playback and requires detected embedded chapters. It skips live/pre-roll/startup-resume work. Supported direct HTTP(S) sources must accept consistent partial ranges; local files also work. Reads stop within bounded request/byte budgets and are cancelled on source/session changes. Successful tables are cached for 24 hours, failures for five minutes, with at most 48 entries. Source addresses/headers are hashed, never saved or logged by this reader. Clearing metadata/all caches invalidates chapter data and in-flight results. [Formats and limits](file-chapters.md).

The CEC adapter is limited to raw Select code 11 in owned S4K browsing/detail windows. A short press waits about 0.32 seconds for release; a hold requires at least 0.65 seconds of repeats and opens context only after release. Other remote codes and fullscreen controls retain their existing path. TV CEC repeat cadence needs testing on hardware.

Pause-rewind no longer seeks while paused. On resume it sends one immediate native relative scrub, without a settling timer, if the same session/file and unchanged position still qualify. Native audio resynchronisation depends on Kodi/device behaviour and must be listened to on Ugoos/Shield.

Validation: all 1,878 automated Windows tests passed, including real local HTTP range/redirect/error responses, large sparse container fixtures, cancellation/cache invalidation, native chapter precedence, remote dispatch, pre-roll cover ownership and pause-rewind guards. Exact-source Linux validation and source-safety CI gate publication. App/skin builds, package/source equality, Python 3.8 parsing, XML, ZIP CRC, credential scanning, feed checksums, Kodi listings and live downloads are separately verified. No physical Kodi device was attached for this audit.

Player skin 0.1.25 and repository installer 1.0.4 retain their published bytes. App 1.8.108 remains available for rollback. No new keys, helper service, profile capture or global audio/display changes are required.

After updating and restarting Kodi, test a named-chapter MKV (wait 5–15 seconds and browse unvisited chapters), short/held TV OK, both pre-roll completion and skip, pause/resume with passthrough audio, collection progress and the next-episode card.
