# Strem4Kodi 1.8.60 audit

The release includes earlier dismissal on owned native video opening, a neutral
cover through pre-roll handover, direct replacement on Skip, and guard tests for
stale intros, delayed callbacks, long intros, cancelled requests and repeated
playback. No global Kodi display setting is changed. HDMI refresh-rate/HDR
blackouts remain device-controlled; this release cannot promise their removal.

The UI audit found a control-ID collision between dynamic hero sizing and the
Add-ons list/actions. Dedicated hero IDs now preserve both layouts. Progress
fills share the explicit watched percentage used by labels. Static headings and
scrolling synopsis have separate geometry with themed alpha fades. Saved-list
refresh runs off the input thread, coalesces duplicate presses and keeps prior
content on failure. Movie watched actions are limited to movie metadata.

Wikipedia attribution and revision links are accessible using Info inside the
same loading window, so no extra modal dialog can remain over playback. The
normal card shows only the fact and an Info hint. Add-ons status uses a static
native colour in both row layouts; descriptions use two complete smaller lines
with bottom padding. Existing title-specific live trivia caching, request bounds,
ten-second rotation and the two-second resume preference are retained.

Validation: 1,189 automated tests passed locally, including actual modal-thread
ownership tests and generated layouts. Release packaging checks cover ZIP
integrity, Python/XML parsing, source agreement, credential signatures and feed
checksums. GitHub validation gates publication. The source repository stays
private; the install feed stays public. Player skin remains 0.1.17.

Android Shield playback, refresh-rate switching and native remote/rendering
behaviour require device confirmation. The current environment has no attached
Kodi device. Restart Kodi after installing this update.

Kodi reference: https://kodi.wiki/view/Settings/Player/Videos#Adjust_display_refresh_rate
