# Strem4Kodi 1.8.110

- Allow delayed first repeats from HDMI-CEC/IR OK holds, retaining one action after release. Require three events spanning 650 ms or a native long-press flag for context; a double tap remains a normal selection. Raw CEC short taps may wait up to 750 ms. Android/keyboard and fullscreen controls retain their existing path.
- Add one bounded numeric OK-gesture summary to existing private diagnostics so device repeat timing can be verified without global debug logging or recording typed keys.
- Remove the fading mask from Up Next artwork and the idle "Play Next when you are ready" text. Keep useful source search/retry/error status messages.
- Replace Watch from Beginning with a clearer skip-to-start icon and a new asset filename to avoid stale Kodi textures.
- Restore recent-search dialogs on Back during the previous selection's input cooldown. Trusted internal navigation bypasses the cooldown while retaining busy-owner, startup and closed-window guards.
- All 1,883 Windows automated tests passed. Package integrity, source equality, Python 3.8 syntax, XML and credential checks passed; exact-source Linux and safety CI gate publication. Physical CEC holds still need a Ugoos retest. Pause-rewind is unchanged and the reported native seek black flash may remain.
- Player skin remains 0.1.25 and repository installer remains 1.0.4. Update the app and restart Kodi.

The published 1.8.109 adapter fails the new regression simulating a 550 ms first-repeat delay, selecting the item prematurely. The revised adapter passes. Actual CEC event cadence is still a hardware verification item; if a device supplies no repeats or native long flag, the Python interface cannot infer a hold reliably. [Behaviour and limits](remote-card-followup.md).

Validation: all 1,883 Windows tests passed in 78.843 seconds. Focused checks covered 11 remote, 60 Up Next, 12 diagnostic-log and five context tests. The 32 px focused/unfocused icon preview was inspected. Exact-source Linux validation and source-safety CI gate the public feed. Package/source bytes, Python 3.8 parsing, XML, ZIP CRC, credentials, feed checksums, Kodi listings and live downloads are separately verified. No physical Kodi device was attached.

The initial Linux release check caught a timing-dependent recent-collection Back failure: if the preceding search set a repeat-draining cooldown, reopening its dialog could be dropped. The internal return now bypasses that cooldown while preserving other-thread busy ownership, startup and closed-window protection. The existing full-controller test forces a future deadline, making this regression deterministic; a new input-guard test covers both the bypass and retained protections. All 56 search-runtime and ten input-settling tests pass on Windows. The final exact-source Linux suite includes 1,884 tests and must pass before publication.

Player skin 0.1.25 and installer 1.0.4 retain their published bytes. App 1.8.109 is kept for rollback. No new keys or profile capture are needed. Update and restart Kodi; retest both short and held TV OK, Up Next artwork/status and the Watch from Beginning icon.
