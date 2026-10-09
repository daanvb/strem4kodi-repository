# Trivia, poster progress and playback preparation — 9 October 2026

Included in app 1.8.54; companion player skin remains 0.1.16.

Loading facts change every ten seconds while the same loading dialog is open.
The rotation pool combines sourced, exact-title local trivia with existing title
metadata, using separate Did you know? and About this title labels. The first
selection still varies between starts. Rotation advances through the pool without
repeating a card before wraparound, retains its current card and deadline across
search-to-playback handover, and stops on cancellation or dismissal. A single
available fact stays in place; no facts means the strip remains absent. There are
no new metadata or stream-provider requests, artwork reloads, focus changes or
loading-window reopenings for rotation.

Title taglines retain italic quotation marks and now have one blank line before
the synopsis. Hidden descriptions, missing taglines and provider descriptions
that already start with the tagline retain their existing behavior. Episode
synopses do not acquire the parent series tagline.

Poster and episode progress tracks now use the same local shape for background
and fill, the current theme accent for fill and a darker track. Native left/right
caps and overlay textures are explicitly blank, avoiding the inherited white
decoration visible above the fill. Progress values and visibility rules are kept.

The supplied device report measured 0.55 seconds finding a source, 17.36 seconds
preparing it and 8.23 seconds opening/buffering in Kodi (26.14 seconds total).
It does not identify which preparation operation was slow. The report now adds
handoff, resolver wait, playback details/context and subtitle preparation timings,
and opens in the larger text viewer so the breakdown is readable. No title names
or stream URLs are recorded; there is still no timer on the loading card.

A verified avoidable startup operation was fixed: forced-only subtitle mode
previously collected external subtitle results before returning without attaching
them. It now returns before that collection and leaves forced-track handling to
the existing post-start watcher. Disabled full captions and disabled automatic
subtitle downloads also skip redundant provider-preference reads. Enabled full
subtitle downloads retain their provider preference and file attachment behavior.
This removes unnecessary work in those modes; it does not establish that subtitles
caused the reported 17-second wait or guarantee faster device playback.

Validation: 1,119 automated tests passed, including ten-second cadence, handover,
single-fact retention, mixed fact labels, preparation breakdown and subtitle-mode
regressions. Native Kodi rendering and a new device preparation report remain
necessary to verify the visible changes and identify the actual slow operation.
