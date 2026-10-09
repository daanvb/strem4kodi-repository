# Strem4Kodi 1.8.64

Autoplay checks explicit show, season and episode information before ranking
sources. Confirmed matches take priority, and remembered sources cannot rescue a
conflicting release. Early series playback waits for a confirmed episode match;
unlabelled results remain a fallback after search and depend on provider accuracy.
Episode-card activation uses the ID of the displayed item rather than a parallel
list offset.

Play Next retains an owned recovery listener through Kodi startup. Failed starts
and recognised provider-error redirects retry another source for the same episode,
within the configured attempt limit. Redirect checks run in parallel with Kodi,
use bounded requests and do not probe live sessions. Stale results cannot stop an
unrelated video or fail a newer attempt. Known rejected attempts are excluded from
watch-progress completion.

Background playback checks avoid querying a file when Kodi is not playing.
Screens without filters skip filter-control lookups.

Validation: 1,211 automated tests passed before release metadata preparation.
Native Android Shield playback, provider redirects hidden by proxies, and the
reported S09E04/S09E05 interaction still need device confirmation. The supplied
log lacked episode/source identity details, so these guards do not establish the
exact cause of that incident. Skin remains 0.1.19. Restart Kodi after updating.

RemuxDB, PublicMetaDB browsing and account sync, native configurable unpause
rewind, and further catalogue/collection search improvements remain pending.
