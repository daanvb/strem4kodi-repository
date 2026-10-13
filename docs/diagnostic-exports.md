# Private client diagnostic reports

Settings > Troubleshooting now includes **Send diagnostic report now**. It requests an immediate upload by the existing service, using the same opt-in and token as automatic reports. Check Diagnostic export for the verified upload result.

Focused app evidence includes the last UI action and allocation/modal/return stage, an app-session marker that survives termination, and short fingerprints of the installed search/window/tag source files. A session without a matching live Kodi lease is reported as interrupted; this can mean a crash, forced close, power loss, or interrupted shutdown, and is not proof of a native crash. Normal closure and caught Python exceptions are recorded separately. Poster diagnostics contain aggregate counts of available award/status/director/chart facts and rendered tag categories.

No titles, queries, URLs, exception messages, paths or session tokens are included in these additional fields. Android native crash dumps still require platform tools; the app cannot obtain those through Kodi's API.

Automatic diagnostic summaries use the existing fine-grained Contents read/write token for daanvb/strem4kodi-sync. The repository must be private; uploads fail closed otherwise. Settings > Troubleshooting includes an opt-out and export status. Without a token nothing uploads.

The service checks every 15 minutes while playback is idle. Each installation receives a random identifier unrelated to hardware or account identity and updates diagnostics/<identifier>.json. Only changed reports upload. Uploads are read back and verified; failures retry on a later check without blocking playback. Git history retains older versions, so deleting a current file does not erase history.

Includes broad software/platform versions, startup/performance timings, last playback stage timings, provider request status/durations, search category result counts, requested IMDb episode identifiers and release episode tags, selected-source format markers and metadata field availability, refresh-rate configuration, bounded counts of known Kodi error/crash patterns from kodi.log and kodi.old.log, and a bounded runtime trace for navigation and playback recovery. Recovery events may include an allowlisted failure reason and outcome plus retry attempt and limit values capped at 25; these fields describe the retry decision without identifying a title, episode, source or URL.

Excludes raw logs, raw exceptions, search text, release filenames, provider configuration, playable URLs, credentials, account details, device names and filesystem paths. Log scanning reads only the final 256 KiB of each log. These are indicators, not a proven crash diagnosis: Android native crash dumps and OS logcat are not accessible through this feature. A crash may prevent upload until Kodi restarts; kodi.old.log then supplies available evidence. An idle check may miss transient session timing before restart.

Reports require authenticated access to the private repository for review. No public issues are created and no LAN access is needed. Automatic exports do not directly probe or fetch media streams.
