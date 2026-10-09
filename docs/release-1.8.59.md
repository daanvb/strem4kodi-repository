# Strem4Kodi 1.8.59 / player skin 0.1.17

The loading card now closes on the current video's AVStarted rather than waiting
for fullscreen and cleared caching. Progressing video with matching attempt or
source identity provides an independent fallback. Dialog lifetime visibility,
isolated temporary layouts and fresh per-playback readiness prevent stale cards
from drawing over video. The companion skin prevents a duplicate busy screen
after the card closes; both packages must update together.

Live trivia uses exact IMDb identity and cited production text from Wikimedia.
The bounded worker, cache, coalescing and error backoff avoid foreground waits.
Facts retain revision links and contributor/licence attribution. Coverage varies
and community citations are not independent verification. Existing sourced
title-specific facts remain an offline fallback.

The release test suite passed: 1,173 tests. Targeted checks exercise callback and
missed-callback dismissal, repeated playback, close/show races, stale ownership,
cancellation, late trivia, generated layouts, identity, API limits and caching.
Package/source agreement, ZIP integrity, Python/XML parsing, credential signatures
and feed dependency/checksum validation are required before publishing. Private
GitHub validation must pass before the public feed is pushed.

No Kodi hardware is attached. Native rendering and remote behaviour require
device confirmation. No universal startup-time improvement is claimed. Restart
Kodi after installing the app and companion updates.
