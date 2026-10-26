# Automatic source hierarchy and episode safeguards

Release 1.8.114. This file records the agreed policy for future
reviews and releases.

Each content profile has an Auto Play priority: Best available quality (default)
or Fastest start. Best available quality compares these stages without weighted sums:

1. Reported video format: P7 or FEL, Dolby Vision, HDR10+, HDR10, other HDR,
   explicit SDR, then unreported.
2. Resolution: 4K, 1080p, 720p, 480p, 360p, then unreported, within the device's
   maximum quality. Any now means highest available within that ceiling.
3. Release: Remux, Blu-ray encode, WEB-DL, WEBRip, HDTV, then unreported.
4. Audio: Atmos, TrueHD, DD+, DD, any DTS format, then other/unreported.
5. Highest reported bitrate, with missing or invalid values last.
6. Largest reported file, with missing values last.
7. Reported provider group: AIOStreams, Usenet, Pengu, then other providers.

Movie, Series and Animated Series retain their preferred video, resolution and
release-type overrides at the corresponding stage. P7 and FEL are interchangeable
preferences, not interchangeable evidence: original reports stay visible. A
community disc hint does not establish the selected file's enhancement layer.

Audio, bitrate/size order and provider order are fixed for autoplay. Their old
per-profile settings are hidden and retained for storage compatibility, but do
not override the hierarchy. Manual picker sorting remains independent. In Best quality a saved
successful source wins only a complete technical/provider tie. Fastest start may
reuse an eligible healthy source confirmed successful within the last 36 hours,
including when starting from the beginning. Older, missing or future-dated
confirmation timestamps get no speed preference. Memory remains local and
stores fingerprints, not playable URLs: a matching row must exist in fresh
cached or currently returned results. Quality mode still ranks the full list.
Temporary provider health penalties break technical ties before provider preference;
they do not promote a lower video, resolution, release, audio, bitrate or size tier.
Per-session failed sources remain excluded from automatic playback.

Best available quality does not start from an incomplete search: a later
provider may return a better release or bitrate. Fastest start can select the
first suitable arrival without waiting for visual, resolution, release or audio
preferences. It still applies every episode, language, failure, filter and ceiling
safeguard. When metadata has a comparable episode title, early playback requires
a matching filename title; number-only files wait for completion. A foreign-only
partial batch does not establish that English is unavailable. Complete cached searches still
use the existing direct selection path. Nothing downloads or probes the video
to invent a bitrate.

## Episode identity in 1.8.140

IMDb series use a cached independent Cinemeta episode map to reconcile displayed
numbering, available episode text and requested video IDs. Artwork preference
does not choose episode identity. Explicit ID/number conflicts block playback
with a clear message; missing reference information retains provider fallback.
Watched-history IDs are not shifted when labels are corrected. The number-only
fallback below remains available after a completed search; filenames and labels
do not establish the actual story contained in a video.

## Episode checks come first

Before ranking, automatic selection excludes local wrong-episode reports,
unsupported disc sources, explicit show-ID/name/season/episode conflicts,
conflicting independent provider filenames, and identifiable multi-episode files.
Metadata-backed complete episode titles can disprove a matching SxxExx label.
Filename vote counts are not evidence. A title-confirmed file is preferred to a
number-only release even if the latter has better technical specifications.

Number-only files remain eligible fallbacks when their episode evidence agrees.
Unlabelled files remain in the manual picker; autoplay needs positive episode
evidence. Unrecognised or ambiguous titles are not guessed to be conflicts.
Reports are reversible through the existing settings workflow.

Release-tag trimming recognises REMUX, Blu-Ray, WEB-Rip, video and audio tokens
even when the filename omits a resolution. Tests cover The Simpsons S09E04 and
S09E05, wrong-title majorities, remembered high-quality wrong files, provider
streamData disagreements and cache round-trips.

## Validation status — 17 October 2026

1,952 full local regression checks pass, including local HTTP integration,
both playback priorities, Up Next,
cancellation/handover guards, timestamp boundaries at 36 hours, setup-profile
round-trips, wrong-episode reports, filename conflicts and cached sources.
The final English-track correction also passes all 27 focused audio/track checks.
Playback chooses labelled English dialogue by the agreed audio tier, then channel
count, preserving the active track on equal quality and respecting manual audio
choices. Missing English leaves the existing fallback available.
Publication is gated on package/source agreement, ZIP integrity, Python/XML,
credentials, exact-source Linux CI and public-feed download verification.
