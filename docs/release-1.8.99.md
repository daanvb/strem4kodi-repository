# Strem4Kodi 1.8.99 / player skin 0.1.24

An approved private setup-profile import queues native Kodi defaults for the next
safe app-shell entry. It enables event logging, HTTP control (kodi username,
empty password, authentication disabled), remote application control on this
system and unknown sources, retaining the existing HTTP port and hardware
preferences. When the companion skin is selected, Kodi Home keeps only Add-ons
and Favourites and enables category widgets. Disc visibility has a reversible
skin toggle. S4K's own navigation menu is unchanged.

Every write follows a durable local backup and is confirmed by readback. Rejected
or unsupported settings remain pending. Skin flags apply only to the active
Strem4Kodi skin. Undo preserves later user edits and retains failed restores.
The private native backup is excluded from diagnostic exports.

Private setup dashboard fixes handle bounded Caddy-streamed form bodies and use
same-origin referrers so a browser login retains its Origin. Origin checks, CSRF,
signed secure cookies and credential-free error diagnostics remain intact.
These backend fixes have already been deployed to the private setup service.

Validation: 30 focused device/setup tests and the full 1,644-test suite passed.
Python 3.8 parsing, XML, source/package agreement, ZIP integrity and credential
checks passed. No physical Kodi device was attached; native prompts remain to be
verified. Restart Kodi after both updates, then import the private profile to
apply these new defaults. Existing devices are not silently reconfigured.
