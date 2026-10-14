# Retention speed, regression, consistency and accuracy audit

Release: 1.8.101; companion skin remains 0.1.25.

Focused checks cover 30/60-day boundaries for incomplete movies, incomplete and
completed series, exclusion of completed movies, exact resume/next focus, expiry
without deleting progress, new playback, refresh stability, missing/invalid legacy
dates, explicit removal, media aliases, live/cached Home, two clients, context
actions and old-index migration. The full 1,678-test app suite passed.

The audit reproduced and repaired three additional defects: lexical ISO ordering
could let an older timezone-offset alias suppress a newer active card; malformed
watch state could raise during Home seeding; cached progress refreshes could move
the reminder row above Upcoming Episodes. Regression cases exercise each path.

Speed work adds a portable SQLite alias projection (no JSON1 dependency), reads
small dates/IDs before loading full displayed metadata, retains existing records
on schema upgrade, reuses one partition for both Home rows, skips unchanged
writes and avoids scanning library histories when no seasonal merge is needed.

Synthetic Windows desktop medians, 4,000 titles with 40-episode metadata for
series: published/pending refresh 383.48/178.73 ms; published Continue Watching
read/pending two-window read 102.69/72.31 ms; reminder merge 3.49 ms. Three refresh
and five read samples were used. The pending read returns up to 100 cards in each
window. These are local measurements, not Fire TV/Shield playback tests.

Python 3.8 parsing, source credential scanning and release ZIP/feed verification
were performed separately. Progress and shared Home removal watermarks remain
intact. No device settings or private metadata configuration are changed by this
app release. Native Kodi rendering still requires a device check.
