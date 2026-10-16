# Reading chapter names from the playing file

The player prefers Kodi's complete `Player.GetChapters` response when that API
is supported. On Kodi 21, it combines Kodi's chapter markers with chapter names
read from the actual source file. No chapter-discovery operation seeks, pauses,
reopens or restarts the native player.

## Discovery and UI behaviour

- One background job per owned movie/episode playback session, after five
  seconds of stable ownership. No file reads for live streams, pre-rolls,
  buffering/paused/seeking players, pending resume operations, or files where
  Kodi detects no embedded chapters.
- A successful table is shared through an addon-owned Home window property.
  Menus perform no network requests or waits. The timeline picks up names
  while open; the chapter picker updates names on its input thread as the user
  browses. Neither update moves the selected chapter or changes Kodi's jump times.
- Names are used only for the same source URL (including its HTTP options),
  with compatible runtime and matching chapter count/markers. Allow 1.5 seconds
  of marker rounding, or 0.01% of runtime for long files. Ambiguous or unmatched
  editions keep native names/numbered chapters.
- Successful results are cached locally for 24 hours, failures for five minutes,
  with at most 48 entries. Signed URLs and request headers are hashed for cache
  identity and never written to the cache or logs. Chapter names/times remain
  local. Clearing metadata/all caches also invalidates this cache and active jobs.

## Supported containers and limits

- Matroska/WebM: flat chapter editions, preferring an unambiguous default
  edition and English chapter displays when supplied. SeekHead offsets locate
  chapter metadata even beyond large video clusters. Known-size clusters can
  also be skipped without an index.
- MP4: Nero `moov/udta/chpl` chapters, versions 0 and 1, including a `moov` atom
  at the end of a large file.
- Direct HTTP(S), local paths and local `file:` URLs. Kodi URL-suffixed
  User-Agent, Referer, Origin, Authorization and Cookie headers are supported.
  Sensitive headers are removed on cross-origin redirects.
- At most 12 range requests, 2 MiB of response bodies, 512 KiB per metadata
  element, an eight-second read budget and socket-operation timeouts of at most
  two seconds. Servers must return consistent HTTP 206 ranges; a whole-file
  HTTP 200 response is closed before reading its body.

QuickTime chapter tracks without a Nero chapter atom, ordered/linked or nested
Matroska chapter editions, SMB/FTP/plugin URLs, and servers rejecting ranges
fall back safely to native/numbered chapters. The existing optional ChaptersDB
menu remains available; it is not needed for supported embedded tables. This
implementation does not require ffprobe or another binary on any client.
