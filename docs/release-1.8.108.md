# Strem4Kodi 1.8.108

- Prevent repeated OK presses stacking identical title screens on slower devices. Load episode cards before optional rating lookups, with bounded background updates that preserve the selected season and focus.
- Confirm real playback position before accepting Resume, retry ignored native seeks within limits, and protect saved progress during failed starts. Preserve resume targets when Kodi briefly reports the previous clip's short duration.
- Strengthen Play Next handover ownership: require the selected playback attempt and a new observed session, handle same-URL episodes and redirects, discard old card data, and ignore late AV-start callbacks from the previous video.
- Automatically capture a diagnostic report after owned playback finishes, stops or errors. Keep the latest ten reports per device, each with its own available redacted Kodi logs. Upload to the existing private GitHub repository while idle; retain offline reports and verify uploads. Existing diagnostic setting and token are reused.
- Reduce diagnostic work during alternating decoder-error floods, keep previous Kodi logs during capture rotation, and remove invalid keyboard keymap aliases. No global decoder/display changes are applied.
- Player skin remains 0.1.25 and repository installer remains 1.0.4. Update the app and restart Kodi. Native Toshiba playback and decoder-error recovery still require device verification.

The existing Automatic private diagnostic reports setting and private GitHub sync token control end-triggered reports. Ten self-contained bundles per client retain bounded, best-effort redacted technical captures from the available Kodi logs. These are not complete raw logs and are not guaranteed anonymous. Offline reports survive restart, oldest reports rotate after ten, and Git history retains older revisions. A process killed by a native crash cannot upload after death; surviving evidence is captured when Kodi restarts. [Capture and retention details](diagnostics-v3.md).

Validation: the integrated Windows suite passed 1,824 tests. Two additional duration regressions then covered the final resume adjustment; all affected Toshiba, progress, diagnostic and cross-listener groups passed. Final exact-source CI validates all 1,826 tests before public publication. App/skin builds, Python 3.8 syntax, XML, package/source byte equality, archive integrity, credential scanning, feed checksums and live downloads are checked separately. No physical Toshiba test has been performed, and these fixes do not prove every native decoder fault resolved.

Player skin 0.1.25 and repository installer 1.0.4 retain their published bytes. App 1.8.107 remains available for rollback. No profile recapture, new API keys or Kodi decoder/display changes are required.
