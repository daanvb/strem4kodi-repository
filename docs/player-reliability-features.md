# Player reliability and convenience additions

Release 1.8.140 preserves owned controls through confirmed redirects and brief
native-player transitions, consumes configured unpause recap once, and requests
skip segments for replacement episodes after an older lookup finishes. The
companion skin 0.1.26 pause button filters repeated activations through Kodi's
native explicit pause/play state, including returning fast-forward to normal
play. Held-Back versus intentional double-Back remains unresolved. Physical
remote timing, decoder/audio behavior and native rendering require device checks.

Automatic VOD playback started from a title or episode page retries another
eligible source after 12 continuous seconds of Kodi-reported buffering while
the owned video is playing and unpaused. It retains the same episode and latest
position, including owned redirects, and uses the existing source-attempt budget.
Pause, missing native observations and replacement playback reset the buffering
observation; explicit cancellation revokes recovery. A stationary playback clock
alone does not trigger a retry. Live sports retain their separate recovery owner.

Up Next freezes its target episode before dispatch, counts preflight rejections against the configured source budget, and retries sources for the same episode. Its card shows searching/checking/starting/retrying status. Stay here invalidates the pending request and closes the card. The existing episode spoiler preference hides the future episode title and thumbnail. This remains a manual Play Next card; no new automatic countdown was introduced.

Player Settings includes Series track preferences: remember current audio/subtitles, or forget them. Preferences are stored locally per IMDb series, with language/codec and subtitle forced/hearing-impaired characteristics, never persistent track indices. Missing matches keep existing selection. Manual menus take priority. Remembering subtitles Off still permits the existing forced-subtitle policy. Applies only to verified Strem4Kodi episodes; no movie/global profile is guessed.

Media info gains automatic-selection details only for automatically selected streams. Source labels are reported evidence, not confirmation of the actual episode contents. Manual selections have no explanation. No explanation appears in search, the source list or loading screen. Existing detected vs reported sections remain distinct. Kodi cache level and audio decoder are shown when available.

Source details show explicit extended/director's-cut/theatrical labels parsed from release information, with no default edition guess. Diagnostic client IDs appear under Troubleshooting; source exhaustion and Up Next failure messages link users to the report reference. Uploaded means a prior verified export exists; pending/new failures may still await the next export. Review full IDs in Settings to locate diagnostics/<id>.json.

Physical-device verification must cover unavailable/changed tracks, forced subtitles, manual selection, skipped pre-rolls, recovery cancellation, and switching titles during source preparation.
