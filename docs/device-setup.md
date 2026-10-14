# Private device setup (1.8.97)

Use the Shield as the master configuration. Its settings are copied through the
app, rather than retrieving its userdata over your home network. This works for
remote clients once the setup service has an HTTPS route.

On the Shield, open Settings → Account & Stremio → Copy setup profile from this
device. Scan the QR code, log into your private setup dashboard and confirm the
code displayed on the Shield. The export includes allowlisted S4K preferences,
API keys, private sync credentials and provider role selections. The service
never receives Stremio sessions, cached streams, user files or custom Kodi keymaps.
Temporary source filters and hardware-sensitive settings are excluded.

On a new device, install the repository, install/open Strem4Kodi, and select
Use my private setup profile. Approve its code on your phone. If sign-in is needed,
the same phone page links to Stremio's official device sign-in. Stremio supplies
the installed private AIO add-ons and library. Existing authenticated devices can
also import the profile from Account & Stremio. Pairing is required each time;
the public repository contains no private keys.

The companion skin remains an addon dependency. The profile remembers whether
the master uses the Strem4Kodi player skin. Kodi appearance is applied at the
next safe app-shell entry, before Home/sign-in allocation. Kodi may require its
normal skin confirmation. Audio, display, remote keymaps and OS permissions
remain device-specific. This does not install Kodi itself or bypass Kodi's
repository/install confirmations.

Approved profile imports also configure Kodi to enable event logging, HTTP
control with username `kodi` and no password/authentication, remote control from
applications on this system, and unknown sources. The existing HTTP port is
retained (Kodi's default is 8080). Remote access from other systems is not enabled
by this profile. Kodi's own confirmation dialogs still apply. Unsupported or
declined settings remain pending and are reported instead of marked successful.

When the profile selects the Strem4Kodi skin, Kodi's Home categories are reduced
to Add-ons and Favourites, with category widgets enabled. Skin changes wait for
that skin to be active; these do not alter the S4K app's navigation menu. Undo
device setup includes these native Kodi and skin settings, preserving subsequent
user edits. The private local backup can contain the previous HTTP password and
must not be included in diagnostic exports.

Client changes are backed up before mutation and retries retain that backup.
Undo device setup restores values still matching the applied profile and keeps
subsequent user changes. Skin undo is queued for the next safe shell entry. Network
failure, rejection, expiration and Cancel do not fabricate successful sign-in.

The Docker setup service uses a separate private admin key, expiring device
requests, per-device secrets stored as hashes, authenticated owner approval,
CSRF protection, no-store responses and bounded request sizes/concurrency.
Successful enrollment can be retried until acknowledged; completed requests
discard their delivery payload. The master profile stays in the private Docker
volume. Enrollment secrets and master keys never appear in QR URLs or logs.

The service's intended origin is https://setup.battleship.live. Route Caddy to
192.168.1.200:8011. The private compose and admin .env are kept separately under
C:/Users/danie/Documents/Codex/s4k-setup; never commit them. The dashboard will
show setting names, not secret values. First copy the Shield profile; empty
profiles cannot silently configure a new device.

The private Docker service and its HTTPS route have been verified. Update to
1.8.97 before copying the Shield profile. The first Shield export and native
second-device enrollment still require testing; no master profile has been
captured automatically.
