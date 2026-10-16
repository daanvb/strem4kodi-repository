# Remote hold and Up Next follow-up — app 1.8.110

Following the user's successful 1.8.109 Ugoos checks for chapter names,
collection progress, pre-rolls and pause-rewind, this patch addresses the
remaining remote/card/icon observations. These changes are included in app 1.8.110.

## CEC hold

The 1.8.109 adapter interpreted 320 ms without another OK callback as release,
including the first event. A regression simulating a 550 ms initial repeat
delay proves that published code selects the item before repeats begin.
The adapter now allows 750 ms for the first repeat and retains a 320 ms quiet
gap thereafter. A context gesture needs three events spanning at least 650 ms,
or an explicit native long-press flag. A double tap cannot become a hold.
Context is still dispatched only after release, to the same active owned
window and focus, so the remaining repeats cannot select its first menu item.
Each handled repeat also marks user activity, keeping idle row work deferred.

This affects raw CEC/IR Select code 11 only. Short taps on that path now incur
up to 750 ms of release inference; normal Android/keyboard and fullscreen
controls are unchanged. Kodi's Python Action interface does not expose CEC
hold duration or a key-release callback. If a CEC adapter delivers only one
event with no long flag/repeats, the addon cannot infer a hold reliably. The
actual Ugoos cadence was not available in the uploaded 1.8.109 report.

One bounded numeric INFO log per completed gesture records event count,
duration, largest repeat gap and context/selection verdict. It contains no
title names, UI contents or typed keys. The existing private report log
extractor retains these fields, allowing hardware retesting without enabling
global Kodi debug logging. No file write occurs for each repeat.

Native references:
- https://github.com/xbmc/xbmc/blob/21.3-Omega/xbmc/interfaces/legacy/Window.h
- https://github.com/xbmc/xbmc/blob/21.3-Omega/xbmc/peripherals/devices/PeripheralCecAdapter.cpp

## Card and icon

Up Next's artwork no longer uses the fading wide mask. Its initial status is
empty, removing "Play Next when you are ready" while retaining useful source
search/retry/error statuses. The episode heading, buttons and safe margins
are unchanged.

Watch from Beginning uses a standard outlined skip-to-start bar/triangle at
256 px. The new restart-v3 filename avoids Kodi's previous texture cache.
Focused and unfocused previews were inspected at the actual 32 px icon size.
The older restart-v2 asset is removed.

## Rewind observation

This patch leaves the functioning native relative rewind seek unchanged.
S4K does not add an overlay, window change or settling timer during this
seek. The reported brief black frame therefore still needs native playback
verification; this patch does not claim to eliminate it.

## Verification

The delayed-repeat regression was run against the published adapter as a
negative control and failed for the expected premature-selection assertion.
The revised adapter passes it. Focused remote, Up Next, diagnostic redaction
and context tests pass. Full-suite and package results are recorded in the
task's remote-card-followup review. Physical short/held TV OK remains to be
verified on Ugoos; these changes are included in app 1.8.110.
