# Strem4Kodi 1.8.98

Up Next now retains the next episode title with thumbnail spoiler protection and
carries corrected names into the next playback payload. Focused episode metadata
skips optional series quality enrichment; credits lookup does not hold the title.
One source search warms during the closing minutes. A preflight in the last 25
seconds can be reused for at most 30 seconds, only for the same episode, playback
session and provider configuration. Preparation cannot dispatch playback; normal
natural-end autoplay, cancellation, source identity checks and recovery remain.

Normal stop preserves the last owned progress sample when Kodi exposes zero or
another video's clock. The primary Play/Resume button and actual dispatch follow
the highlighted episode. Watched history no longer suppresses an explicitly
unfinished rewatch. Optional service task failures are isolated; shutdown no longer
references the removed format worker. A native Home retirement timeout blocks the
next full-window allocation. Search copies only related prefix-cache rows and hero
metadata is bounded to 64 recent titles.

Validation: all 1,632 tests passed on Windows with Python 3.12/Pillow 12.3.0.
Package integrity, source credential checks and Python 3.8/3.11 grammar checks
passed. Physical Fire TV progress rendering and handoff speed remain unverified.
Player skin remains 0.1.23; restart Kodi after updating.
