# Near-zero poster progress

Unpublished rendering correction. No playback records, percentages, positions or
completion thresholds are rewritten.

The card mapper keeps an unfinished item visible with WatchedProgress at least
1, while Kodi's native ListItem.PercentPlayed rounds the actual bookmark ratio
to a whole percent. A two-hour film stopped after 1, 5, 15 or 30 seconds therefore
has a visible track but native progress zero.

In stretch mode, Kodi sets the fill texture's width to zero. GUITexture then
interprets zero width as the source texture's intrinsic width, 170 pixels for
our capsule. On a 192-pixel poster bar this is 88.54%, matching the reported
almost-full appearance. This explains a reproducible rendering failure; the
affected client's stored progress was not retrieved to prove its exact state.

All generated poster/wide/grid bars and the six bundled Home/details bars now
use clipped reveal. The fill keeps its full control width and is clipped to the
actual percentage; an empty zero-percent clip suppresses rendering. Track/fill
colours, the native bookmark and focus geometry remain the same. The existing
Home layout digest includes poster_progress.py, invalidating generated cached
layouts automatically.

Primary Kodi 21.3 sources:
- [Native rounding](https://github.com/xbmc/xbmc/blob/21.3-Omega/xbmc/guilib/guiinfo/VideoGUIInfo.cpp#L48)
- [Progress layout and clipping](https://github.com/xbmc/xbmc/blob/21.3-Omega/xbmc/guilib/GUIProgressControl.cpp#L207)
- [Zero-width texture sizing](https://github.com/xbmc/xbmc/blob/21.3-Omega/xbmc/guilib/GUITexture.cpp#L353)

Validation: 42 focused tests passed across poster rendering, fast Home progress
refresh and watch-progress saving. Checks use production state updates and card
mapping, generated final layouts in every theme, and a model of the native
zero-width/clipping behaviour at 0%, 1%, 50%, 90% and 99%. The old stretch mode
reproduces 170/192 at zero; clipped reveal yields zero. This is not a physical
Fire TV GPU render. App/package checks are recorded with the unpublished build.
