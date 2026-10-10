# Strem4Kodi 1.8.70

Improve native Left/Back navigation, search scrolling, result ordering and stale search-state cleanup. Buffering settings now open Kodi cache settings, and owned live-player controls hide subtitles.

Reject recognised AIOStreams static error videos while keeping inconclusive probes available to Kodi. Strengthen playback error and pre-roll callback ownership so stale sessions cannot interrupt a newer video. Bind queued progress to the account that created it and tolerate optional embedded-source storage failures.

Player skin updates to 0.1.22. Restart Kodi after updating. Automated tests and package checks run on Windows, with exact-commit Linux CI required before publication. Real Kodi device UI, remote focus, decoder and cross-platform playback remain unverified.
