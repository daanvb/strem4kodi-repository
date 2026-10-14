# Strem4Kodi 1.8.101

Continue Watching now uses a last-playback clock for movies and series. At 30
days without playback, cards move to Don't Forget About Me; at 60 days, they
leave Home without deleting progress, history or saved lists. New playback resets
the clock. Explicit media aliases prevent duplicates, including timezone variants,
and moved cards retain resume/next-episode focus and contextual removal.

The audit also corrected malformed-state handling, cached Home row order and
older-index alias migration. Home reuses one partition read, loads full metadata
only for displayed cards and avoids writes for unchanged records.

All 1,678 automated tests passed. A 4,000-title synthetic desktop benchmark
measured unchanged refreshes at 179 ms versus 383 ms in 1.8.100, with reminder
merging at 3.5 ms. These figures do not measure TV hardware. Python 3.8 parsing,
credentials, package/source agreement and repository integrity were checked.
No physical Kodi device was attached; device rendering and speed need a retest.
Skin remains 0.1.25. Restart Kodi after updating; no profile recapture is required.
