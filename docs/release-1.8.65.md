# Strem4Kodi 1.8.65

The supplied Shield log records a fatal native Kodi exit caused by concurrent
busy dialogs. It contains one media OpenFile request and two distinct custom
loading layouts during startup; it does not prove multiple media launches or
identify a wrong episode file.

Autoplay and Play Next now defer source recovery while Kodi's native busy dialog
is active, even before video is reported as playing. Recovery requests Stop once
for an owned failed video and waits for shutdown before retrying another source
for the same episode. Unrelated playback is left alone. If startup remains busy
for 15 seconds, or Stop has not completed after five seconds, automatic recovery
ends with a clear message.

Loading dialogs are serialized across sessions. Replacements wait for the prior
modal loop and native close call to finish, and avoid opening during Kodi's native
startup wait. Cancel can terminate a queued loading card before construction.

Validation: 1,219 automated tests passed, including busy startup before playback,
asynchronous Stop, delayed modal return, delayed native close and Play Next retry
identity. Package integrity, source agreement and release feed checks are required
before publication. Native Shield behavior still needs device confirmation.
Player skin remains 0.1.19. Restart Kodi after updating.

RemuxDB, PublicMetaDB browsing and account sync, native configurable unpause
rewind, and further catalogue/collection search improvements remain pending.
