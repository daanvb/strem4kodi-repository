# Private diagnostic capture

This extends the existing opt-in Automatic private diagnostic reports setting
and private sync token. It does not enable Kodi debug logging or upload to a
public repository. A successful PUT alone is insufficient: the uploader reads
each attachment and report back and verifies its bytes.

## Evidence

- The existing strict JSON excerpts and counts remain available.
- Larger compressed technical logs preserve unfamiliar warning/error text,
  traceback locations, native decoder/GUI errors and known app transitions.
  Unknown ordinary INFO/DEBUG chatter and serialized payloads are excluded.
- URLs, common credential fields, configured keys, paths, email/IP addresses,
  quoted strings and long opaque values are scrubbed. Free-form error messages
  are best-effort redacted, **not guaranteed anonymous**. They belong only in
  the private repository. Never republish these attachments wholesale.
- Identical consecutive errors are condensed with repetition counts and the
  last timestamp. Earlier distinct errors survive an error flood.
- Six redacted compressed snapshots survive restarts locally. On upload these
  occupy six stable `diagnostic-logs/<client>/<0..5>.log.gz` slots; each report
  lists the source, capture time, SHA-256, lengths and truncation state. Match
  the hash to the report, or use Git history if a slot was subsequently updated.
  Git history is not automatically pruned.
- Each Kodi log read is limited to 1 MiB (first 64 KiB plus the end for a large
  log); each technical text is limited to approximately 256 KiB. Truncation is
  explicit. A partial first/last line at the splice is discarded.
- Collection starts after service initialization and repeats every minute on
  a background worker, including during playback. Unchanged files are skipped.
  Network uploads run while idle every 15 minutes, on the first idle check
  after service restart, or when explicitly requested. Upload opt-out/token
  changes are checked again before each write. Failed uploads retain local
  evidence for retry. This is bounded retention, not an unlimited flight recorder.

## App failure and transition evidence

App error handling, addon worker exceptions, service task failures, source
search/render failures and progress queue write failures retain package-relative
stack locations and error classes. Exception values, media identities, typed
searches and source URLs are not included in these fixed-field events. Repeated
identical failures are rate limited. Existing Kodi thread error handling remains
in place; no fatal-signal handler is replaced.

Existing UI/session markers cover Search, title allocation, Back and collections.
Additional persistent events cover source-panel opening/refresh, resolver and
playback handoff/cancel, final progress queuing, and Play Next card allocation,
click, listener construction, searching, selection, dispatch, confirmed start
and close. These identify the last observed step; they do not alone prove why
Kodi exited. A progress-queued event confirms the local queue, not remote sync.

## Startup speed evidence

The last 12 launches retain fixed numeric offsets in milliseconds from program
entry: splash, settings, account/setup, imports, cached Home, layout, initial
Home visible, catalogue refresh (`background`), refreshed UI (`background_ui`)
and poster refresh completion (`background_art`). Subtract consecutive offsets
to locate time spent in each stage. Setup/login user interaction can be included
in the account stage. Missing background stages can reflect navigation away or
cancelled/stale work rather than a failure. Initial visible means the Home
initialization checkpoint, not a measured GPU presentation timestamp.

First launch in a Kodi session and repeat launches are distinguished. Readiness
milestones save a small bounded record, not a per-frame/per-key disk trace.
Background work belonging to an older launch cannot amend a newer launch.

## Android / Fire OS limits

On each service start and manual report, attempt the accessible Android crash
buffer with `/system/bin/logcat -b crash -d -t 200 --uid=<Kodi UID>`, a three-second
timeout and bounded output. There is no shell, root escalation or other-app
collection. A status distinguishes capture, no accessible entries, unsupported
or denied access, timeout and unavailable tooling. Raw subprocess errors are
not exported. Native crash records owned by Android's crash collector or OS
memory-kill records may be inaccessible. A Kodi addon cannot guarantee those
records, binary tombstones or a report from a process after it has died. Reopen
Kodi promptly after a crash so its surviving evidence can be captured and sent.

The Fire TV Play Next exit reported before this change remains unconfirmed.
The old filtered reports cannot restore messages that were already omitted.
