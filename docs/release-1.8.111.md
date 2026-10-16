# Strem4Kodi 1.8.111

- Add Playback > Rewind when resuming saved progress: Off (default), 3, 5, 10, 15, 20, 30 seconds or 1 minute. Start movies/episodes before their saved position, including Continue Watching, without a delayed extra seek or cumulative rewind during startup retries. Short positions clamp to the beginning; fresh plays, new episodes, live streams and pre-rolls are unaffected. Include the preference in setup profile copies.
- Put Settings time choices in ascending order, including trailer delay, control-bar timeout and custom cache lifetimes. Keep existing saved selections, defaults and profile values unchanged.
- Scroll Home rows before the focused poster reaches a clipped right-edge slot, for both portrait and wide layouts.
- Restore saved artwork and title/collection identity in Recent Searches without background metadata requests. Existing text-only history gains artwork when a title is selected again.
- Use clear eye/crossed-eye context icons for watched/unwatched actions, with versioned artwork to avoid stale Kodi textures.
- Automated Windows regression checks, exact-source Linux CI, package/source consistency, syntax/XML, archive integrity, credential checks, feed checksums and live downloads gate publication. No physical TV was attached for this audit.
- App 1.8.111; player skin remains 0.1.25 and repository installer remains 1.0.4. Update the app and restart Kodi. Viewer profiles remain design-only.

Validation: all 1,899 Windows tests passed. The settings tests exercise every displayed selection for reordered enums, verifying that it writes the original saved value and reopens with the correct selection. Cache custom durations retain their exact string values. Resume checks cover all durations, invalid settings/progress, source retries, unchanged inputs, native StartOffset/ResumePoint (including zero), live/new-play exclusion and setup profile export. Existing playback/progress, pre-roll, chapter, Search Back, input ownership and remote tests remain in the full regression suite.

The audit also checks generated row bounds for both portrait and landscape layouts, selected title/collection artwork and identity across recent-search reopen/clear, and action asset references. Package/source equality, Python 3.8 syntax, XML, ZIP CRC, credentials, feed metadata and live downloads are verified separately. Exact-source Linux validation and source-safety CI must pass before the public feed is pushed.

The legacy Kodi addon-settings XML retains its stored enum ordering to keep old values and setup profiles compatible. The app's own Settings displays durations chronologically. Resume rewind changes only the playback request; normal progress recording begins after playback as usual. Unpause rewind itself is unchanged.

After updating/restarting, choose Settings > Playback > Rewind when resuming saved progress, then test a partially watched movie/episode. Check both a normal saved position and one shorter than the recap. Check trailer/control timeout choices, custom cache lifetime ordering, Recent Searches posters, watched/unwatched icons and the last focused poster in Home rows.

No physical Kodi device was attached. This release does not claim to resolve native decoder/seek black frames. Skin 0.1.25 and installer 1.0.4 retain their original published bytes. App 1.8.110 is retained for rollback. Viewer profiles are a proposed design, not an available feature. No new API keys are needed.
