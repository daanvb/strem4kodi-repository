# Strem4Kodi 1.8.107

- Preserve larger redacted Kodi technical logs, including unfamiliar warning/error details, across restarts. Condense repeated errors while retaining the first fault and final context.
- Retain up to six compressed log snapshots per client and upload verified attachments to the existing private GitHub repository. Capture locally on restart/every minute, skip unchanged files, and keep automatic network uploads idle-only. Existing diagnostic opt-in and token are required.
- Attempt Kodi-only Android crash-buffer capture on service startup and manual reports. Report unavailable, restricted or missing evidence explicitly; no root access, other-app logs or binary crash dumps are collected.
- Add persistent Play Next, source selection, resolver, cancellation and progress-queue checkpoints, plus safe app/service/worker error classes and code locations. This instrumentation does not claim the reported Fire TV Play Next crash is fixed.
- Record the last twelve first/repeat startups, from splash/settings/account and cached Home through first visible Home, catalogue refresh and artwork completion. Buffer stage timings and avoid per-frame logging.
- Player skin remains 0.1.25 and repository installer remains 1.0.4. Update the app and restart Kodi. After another crash, reopen Kodi promptly so surviving evidence can be captured and uploaded.

The existing Automatic private diagnostic reports setting and private sync token are reused. Larger logs are best-effort redacted, not guaranteed anonymous; unfamiliar free-form error text can still contain personal information. They are uploaded only after verifying the destination repository is private. Snapshot bounds, retention, hashes, missing-evidence statuses and startup stage meanings are documented in [diagnostics v3](diagnostics-v3.md).

Validation: the integrated Windows regression run and focused repaired/new cases are recorded in [diagnostic validation](diagnostics-v3-validation.md). Final source validation and source-safety CI gate public publication. App/skin builds, package/source byte equality, Python 3.8 parsing, XML, ZIP CRC, credential checks, repository metadata and Kodi file-browser listings are verified separately. No physical Fire TV test has been performed. Android crash-buffer access may be restricted; an abrupt native/process exit cannot be captured after the process has died.

Player skin 0.1.25 and installer 1.0.4 retain their published bytes. App 1.8.106 is retained for rollback. No profile recapture, API key changes, global debug logging or playback/display setting changes are required.
