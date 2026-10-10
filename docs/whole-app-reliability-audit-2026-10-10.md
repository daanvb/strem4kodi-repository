# Whole-app reliability audit — 10 October 2026

Reviewed playback attempt ownership, episode identity, retry/cancellation, pre-roll handoff, provider response validation and cache fallbacks, resolver IPC, account concurrency and refresh, queued progress ownership, background sync and cleanup, Search grouping/return navigation, native grid navigation, settings and live-player focus.

Confirmed fixes:

- Bind queued progress to its hashed account owner before network access, preventing an account-switch race from sending old progress to a new account.
- Reject foreign or unrelated AV/Error callbacks before changing the selected attempt, marking playback successful, or clearing its handoff. Require ownership before a pre-roll callback suspends the startup timeout.
- Preserve embedded playable sources when optional badge storage is locked or read-only.
- Clear stale Search return snapshots when the user chooses another browse section.
- Recognise exact bundled AIOStreams failure-video paths in existing probes and recovery; retain inconclusive HTTP response deferral and same-episode retries.
- Preserve native grid edge actions rather than numeric self-navigation, group collections/lists before media, and restore Search query/results/selection after a collection excursion.
- Expose Kodi's global cache controls from the player and Playback settings; hide subtitles only for live-player controls.

Regression coverage includes deterministic account-switch and stale-callback races, locked-storage fault injection, Search restore/rebuild, and existing Windows multiprocess account locking. The final pre-roll fixture correction models the ownership properties set by the actual native ListItem; production safeguards were retained.

Isolated unpublished package validation passed source agreement, Python/XML parsing, ZIP integrity, known credential signatures, declared versions and feed checksum checks. These audit packages use the current development manifests and must not replace released packages.

Automated execution was on Windows. Cross-platform code review considered Kodi-translated profile paths and Windows/POSIX locking. Android, Windows, Linux and other supported Kodi 21+ devices still require real remote/navigation, decoder, display-switching and live-stream checks. No device execution is implied by unit tests or code review. This is a risk-focused audit, not proof that every possible defect is absent.
